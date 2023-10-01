# Minimalish Django Starter

## why

you are like me and want to _quickly_ start working on - and deploy! - a minimalish Django project. wow you've literally come to the right place.

this django "**project template**" ((it's really confusing to use the word "template" because it's not a ... [template](https://docs.djangoproject.com/en/4.2/topics/templates/)...)) is based on / assumes you also want / is made out of the following:

- django 4.2 (not married to this version, it's just very modern and version 5 juuust came out so I'll hang around 4.2)
- python 3.10/.11 ish
- pip / venv / requirements.txt - tried and true, it works, etc.
- .env configuration files on developers' machines using `python-dotenv`
- os-level env vars on production
- TODO dev/prod separation in the settings
- postgres via `psycopg2-binary`
- postgres database url set via env var thanks to `dj-database-url`
- TODO custom user model (because you only get [one chance](https://docs.djangoproject.com/en/4.2/topics/auth/customizing/#changing-to-a-custom-user-model-mid-project))
- use of `os.environ[]` rather than the softer `os.getenv()` which by design silently fails. if an env var can't be found, that's a problem that needs addressing
- TODO whitenoise

bonus round

- configuration file to deploy all of this to render.com!! - they are like heroku used to be i.e. good

## what

## how

to initiate a new Django project using this starter kit template:

```bash
echo -n "what's your project name? "
read PROJECTNAME
python3 -m venv venv
source venv/bin/activate
pip install Django==4.2.5
django-admin startproject --template=https://github.com/gregsadetsky/minimalish-django-starter/archive/main.zip -n ".env.example" $PROJECTNAME .
pip install -r requirements.txt
mv starter $PROJECTNAME
git init
```

then:

- duplicate `.env.example` to `.env` and fill it out
- create the appropriate postgres database locally
- run `python manage.py migrate`
- start the server with `python manage.py runserver`
- do good work

finally:

- git add/commit/push to a new repo
- go to render.com, create a new "blueprint instance" and point it to your repo
- you should be live!!

## misc/extra bonus

- assuming you're using black (via an auto-save package in your editor)
- also recommend using pyright (via your editor)

## other resources

- https://12factor.net/ - started it all
- https://github.com/cookiecutter/cookiecutter-django - exactly like this, "Cookiecutter Django is a framework for jumpstarting production-ready Django projects quickly" - but too much-y for my taste. it's great! I just wanted my own so I made this.
- https://github.com/jefftriplett/django-startproject - similar to this as well

## huh

this project was done during my time at the [Recurse Center](https://recurse.com/)
