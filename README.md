# DJ_PARSER | WEB

**Зпускается файлом `dj_parser\uv_server.py`**

Либо `python manage.py runserver`

admin: `ahab:2255AXAX`

## Подготовка:

```
python -m venv venv_parser

.\venv_parser\Scripts\activate

python -m pip install --upgrade pip

pip install -r requirements.txt 
```


## Флоу действий:

Создал шаблон index.html

Добавил настройки settings.py: `"DIRS": ['templates'],`

Создал приложение `myapp1`: `python manage.py startapp myapp1`

и зарегистрировал его в `settings.py`:
```
INSTALLED_APPS = [
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
    "myapp1",
]
```

Добавил функцию в `views.py` в `myapp1`:
```
TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": ['templates'],
...
```

Зарегал эту функцию в `settings.py`:
```
from django.contrib import admin
from django.urls import path
from myapp1.views import index_page

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", index_page),
]
```

`python manage.py createsuperuser`

`models.py`:
```
class Parsing(models.Model):
    title = models.CharField(max_length=63, blank=False)
    link = models.CharField(max_length=255, blank=False)
    
    def __str__(self):
        return f'T :: {self.title}'
```
Далее выводим в `context` во `views.py`

---

## Прочие команды:
```
python -m venv venv_parser
python3 -m venv venv_parser

.\venv_parser\Scripts\activate
source venv_parser/bin/activate

python -m pip install --upgrade pip
python3 -m pip install --upgrade pip

pip install -r requirements.txt | pip freeze > requirements.txt


.\manage.py runserver 

python -m uvicorn dj_parser.asgi:application

python manage.py migrate
```

```
WSGI_APPLICATION = "dj_parser.wsgi.application"

ASGI_APPLICATION = "dj_parser.asgi.application"
```

---

Models:

ID Title Link