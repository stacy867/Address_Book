# GET STARTED #
After developing a Django application, my next step was to make it live and available for the users.I used Heroku platform to for deployment

## Prerequsite
Before you dive into deploying django application using Heroku, you should set up a virtual environment for your Django project and make sure you activate the virtual environment that was created.

step 1:
Download python
step 2:
Download virtual environment:
>$pip install virtualenv
step 3:
Name your virtual environment:
>$python -m venv venv
step 4:
Turn on Virtual Environment:
>$source venv/Scripts/activate

## Deployment
# step1:
Execute the pip freeze command to show all installed files and copies them into a file called requirements.txt:
>$pip freeze >requirements.txt
<br>
the followingis for viewing the files:
>$cat requirements.txt

# step2:
check if heroku is installed in cmd:
>heroku -h

# step3:
In the Address_Book(Django project) go to settings.py at the end of the file add the following statement:

>STATIC_ROOT = os.path.join(BASE_DIR, ‘static’)

Django is unable to automatically create a target directory i.e. STATIC_ROOT. Hence, in ‘settings.py’, a variable called ‘STATIC_ROOT’ is responsible for defining the single folder where you are willing to collect all your static files.

# step4:
Add a procfile file :
>$nano Procfile (to create and edit the Procfile)

open the file in your project and add the following:
>web: gunicorn Address_Book.wsgi

Here, the created ProcFile requires a Gunicorn as it is one of the most preferred production web server for Django applications.

# step 5:
Install gunicorn:
>$pip install gunicorn 
<br>
Include it in the requirement.txt:
>pip freeze >requirements.txt
<br>
check if it is there:
>cat requirements.txt

# step 6:
Install django-heroku:
>$pip install django-heroku
‘django-heroku’ package is able to carry out the configurations part automatically which allows your Django application to work Heroku.

update the requirements.txt file:
>$pip freeze > requirements.txt
<br>
>$cat requirements.txt

# step 7:
import the following packages in settings.py at the top of the file:
>import os
>import django_heroku

# step 8:
To activate django_heroku at the end of the settings.py file add the following line of codes:
>#Activate Django-Heroku.
>django_heroku.settings(locals())

# step 9:
Since, you are now moving onto the production site, the ‘DEBUG’ in ‘settings.py’ should be set as ‘FALSE’:
>DEBUG= False

# step 10:
To initialize a new or empty repository:
>$git init
<br>
To add all the files from your directory:
>$git add .
<br>
Commiting changes and nan=ming the commit:
>$git commit -m "deploy"

# step 11
Login to heroku:
>$heroku login

After you have executed the command ‘heroku login’, in the web browser, you are now redirected to the page as shown
in the image below. Here, you are required to click on the ‘Log In’ button.

# step 12
Now you are required to create an app in Heroku i called it address-book-2:
>$ heroku create address-book-2

# step 13
After successfull execution of the command i was able to view my applicatin in heroku

# step 14
Push the directory for deployment
>$git push heroku master

# step 15:
Commited initial migration on the heroku application:
>$heroku run python manage.py migrate

# step 16:
Finally run the application:
>$heroku open

You are required to allocate the allowed hosts or domain which your Django application serves,in settings.py,it prevents the web application from HTTP Host Header attacks.

>ALLOWED_HOSTS = ['https://address-books2.herokuapp.com/',
>'localhost',
>'127.0.0.1']







