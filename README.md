# apscheduler


## Si vous suivez ce tuto cela suggere que vous avez creer un projet et une application Django. Et effectuez toutes les configuration

## Installons apscheduler

  ```python
    pip install apscheduler
  ```
  
  
## Dans votre application
- Creer un dossier forecastUpdater
- Dans forecastUpdater creer 2 fichiers 
  -__init__.py
  -forecastApi.py
## Dans le fichier forecastApi.py
  Nous allons creer une fonction qui contient la tache que nous aimerons executer en arriere plan
  ex: une fonction qui return hello world
  
  ```python
  def update_forecast():
    return "hello world"
  ```
  
  ## Creer un fichier updater.py dans le dossier forecastUpdater
  
  Dans ce fichier nous allons appeler notre fonction et lui appliquez les possibilite de apscheduler
  ```python
    from apscheduler.schedulers.background import BackgroundScheduler
    from forecastUpdater import forecastApi

    def start():
        scheduler = BackgroundScheduler()
        scheduler.add_job(forecastApi.update_forecast, 'interval', minutes=5)
        scheduler.start()
  ```
  Notre fonction s executera chaque 5 minuites grace a " 'interval', minutes=5 "
  
  ## Dans notre application nous avons le fichier apps.py
    -dans ce fichier ce code a la fin
    ex:
      ```python
          def ready(self):
            from forecastUpdater import updater
            updater.start()
      ```
      
     
