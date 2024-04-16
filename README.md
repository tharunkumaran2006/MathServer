# Ex.05 Design a Website for Server Side Processing
## Date:05/04/2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
### math.html:
```
<html>
<head>
    <style>
        body 
        {
            font-family: Arial, sans-serif;
            background-color:rgb(241, 143, 14);
            color: rgb(104, 14, 208);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 150vh;
        }
        .box 
        {
            background-color:rgb(7, 198, 147); 
            border-radius: 8px;
            box-shadow:rgb(218, 10, 93); 
            padding: 70px;
            width: 500px;
        }
        h1
        {
            color:rgb(218, 11, 149);
            text-align: center;
            padding-top: 40px;
        }
        h1:hover
        {
            color:rgb(217, 8, 8);
        }
        </style>
</head>
<body>
    <div class="edge">
    <div class="box">
    <U><h1>Tharun V K (212223230231)</h1></U>
    <h2>SURFACE AREA OF RIGHT CYLINDER</h2>
    <form method="POST">
        {% csrf_token %}
        <div class="formelt">
        Radius: <input type="text" name="radius" value="{{r}}"></input><br/>
    </div>
    <div class="formelt">
        Height: <input type="text" name="height" value="{{h}}"></input><br/></div>
    <div class="formelt">
    <input type="submit" value="Calculate"></input><br/></div>
    <div class="formelt">
        Area: <input type="text" name="area" value="{{area}}"></input><br/>
    </div>
</form></div>
</div>
</body>
</html>
```
### views.py:
```
from django.shortcuts import render
def surfacearea(request):
    context={}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        r = request.POST.get('radius','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('Radius=',r)
        print('Height=',h)
        area = 2*3.14*int(r)*int(h)+2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area=',area)
    return render(request,'mathapp/math.html',context)
```
### urls.py:
```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfaceareaofrightcylinder/',views.surfacearea,name="surfaceareaofrightcylinder"),
    path('',views.surfacearea,name="surfaceareaofrightcylinderroot")
]
```
## SERVER SIDE PROCESSING:
![Screenshot 2024-04-16 183246](https://github.com/tharunkumaran2006/MathServer/assets/151625188/f04f4943-32ea-48eb-9486-591f84c58eda)


## HOMEPAGE:
![Screenshot 2024-04-16 183055](https://github.com/tharunkumaran2006/MathServer/assets/151625188/bed563c6-08ea-4fda-a29c-6be512f9c1e1)


## RESULT:
The program for performing server side processing is completed successfully.
