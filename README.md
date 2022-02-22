# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Desing your website for calculation using wireframe work.
### Step 2:
Then to execute the wireframe work desing use html,css 
### Step 3:
Use views.py to execute the coding in serverside.
### Step 4:
Mention the path of the website in urls.py.
### Step 5:
Publish the website in the given URL : http://pragatheesh.student.saveetha.in/

## PROGRAM :

### Volume.html:
```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Math Calculation</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <script src='main.js'></script>
    <style>
        * {
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}
body {
  background-image: url("/static/img/maths.jpg");
}
.container {
  width: 1080px;
  margin-left: auto;
  margin-right: auto;
  padding-top: 200px;
  padding-left: 300px;
}
.content {
  display:block;
  width: 500px;
  min-height: 300px;
  font-size: 20px;
  background-color:white;
}
h1{
    color: blue;
    text-align: center;
    padding-top: 25px;
}
.formelement{
    color: blue;
    text-align: center;
    margin-top: 5px;
    margin-bottom: 5px;
}
    </style>
</head>
<body>
    <div class="container">
    <div class="content">
    <h1>VOLUME OF A CUBOID</h1>
    <form method="POST">
        <div class="formelement">
        Length : <input type="text" name="length" value="{{l}}"></input>Meters<br/>
        </div>
        <div class="formelement">
        Breadth : <input type="text" name="breadth" value="{{b}}"></input>Meters<br/>
        </div>
        <div class="formelement">
        Width : <input type="text" name="width" value="{{w}}"></input>Meters<br/>
        </div>
        <div class="formelement">
        <input type="submit"  value="Calculate Volume"></input><br/>
        </div>
        <div class="formelement">
        Volume : <input type="text" name="volume" value="{{volume}}"></input>Meter<sup>3</sup><br/>
        </div>
    
    </form>
    </div>
    </div>
</body>
</html>

```
### Views.py:
```
from django.shortcuts import render

# Create your views here.
def volumecalculation(request):
    context={}
    context['volume'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    context['w'] = "0"
    if request.method == 'POST':
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        w = request.POST.get('width','0')
        volume = int(l) * int(b) * int(w)
        context['volume'] = volume
        context['l'] = l
        context['b'] = b
        context['w'] = w
    return render(request,'mathapp/volume.html',context)
```
### urls.py:
```
"""calculation URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/3.1/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('volumeofacuboid/',views.volumecalculation,name="volumeofacuboid"),
    path('',views.volumecalculation,name="volumeofacuboidroot")
]

```

## OUTPUT:
![Output](.//output.png)

## Result:
Thus a website is designed to perform mathematical calculations in server side is successful.
