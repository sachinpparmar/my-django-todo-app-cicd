# django-todo
A simple todo app built with django

![todo App](https://raw.githubusercontent.com/shreys7/django-todo/develop/staticfiles/todoApp.png)
### Setup
To get this repository, run the following command inside your git enabled terminal
```bash
$ git clone https://github.com/shreys7/django-todo.git
```
You will need django to be installed in you computer to run this app. Head over to https://www.djangoproject.com/download/ for the download guide

Once you have downloaded django, go to the cloned repo directory and run the following command

```bash
$ python manage.py makemigrations
```

This will create all the migrations file (database migrations) required to run this App.

Now, to apply this migrations run the following command
```bash
$ python manage.py migrate
```

One last step and then our todo App will be live. We need to create an admin user to run this App. On the terminal, type the following command and provide username, password and email for the admin user
```bash
$ python manage.py createsuperuser
```

That was pretty simple, right? Now let's make the App live. We just need to start the server now and then we can start using our simple todo App. Start the server by following command

```bash
$ python manage.py runserver
```

Once the server is hosted, head over to http://127.0.0.1:8000/todos for the App.

Cheers and Happy Coding :)

------------------------------
"" virtualenv -p python3 env
 source env/bin/activate
 cd django-todo/
 python manage.py makemigrations
 pip install djando ""

source env/bin/activate     "for activate env"
python manage.py runserver 0.0.0.0:9000                    "for port"

pip freeze > requirements.txt                "for requirements.txt file it create a file with version you req"


token     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
         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
         ------------------------------------------
   ------------------------
----------------------------------------------------------------------------------------------------
   ##if we run on minikube 
   
   # deploy.yml
   
   apiVersion: apps/v1
kind: Deployment
metadata:
  name: todoapp
  labels:
    app: todoap
spec:
  replicas: 3
  selector:
    matchLabels:
      app: todoapp
  template:
    metadata:
      labels:
        app: todoapp
    spec:
      containers:
      - name: todoapp
        image: sachin11parmar/mytodoapp
        ports:
        - containerPort: 8000
  
  
 # service.yml 
 
 apiVersion: v1
kind: Service
metadata:
  name: todo-service
  labels:
    app: todoapp
spec:
  type: NodePort
  selector:
    app: todoapp
  ports:
    - port: 8000
      targetPort: 8000
      nodePort: 30007
      
 ---------------------------------------------------------------------------------------
   
   #for port-forward  in k8s
kubectl port-forward svc/todo-service 8000:8000 --address 0.0.0.0

------------------------
##Live DevOps Project for Resume - Jenkins CICD with GitHub Integration (Notes) (TrainWithShubham)

notes-link     https://docs.google.com/document/d/1qos4eUfY4vZojjnZLSGw8D3A46Yy2r42uiZPyPxL17A/edit
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------------------------
## todo list app steps 
 git clone https://github.com/sachinpparmar/django-todo.git
    sudo apt update -y
    pip install django
    pip3 install django
   sudo apt install python3-pip
   sudo apt install python3-pip3
    pip3 install django
    python3 manage.py migrate
    pip show django
    python3 manage.py runserver
    python3 manage.py runserver 0.0.0.0:8000       "if error come for web page use "*" in settings.py   ( cd todoApp vi settings.py) " 
    vi todoApp/settings.py   ##and add '*' in []
    python3 manage.py runserver 0.0.0.0:8000
   python3 manage.py runserver 0.0.0.0:8000     
   # check with public ip with 8000   public-ip:8000 on google it shows web app page 
    nohup python3 manage.py runserver 0.0.0.0:8000 &   ## if u want to run in  backround  so use this nohup & concept 
    
   ## if you want to check 8000 port running or not or other info..   so we use this command  "it listed the running services on this port"
    lsof -i:8000
    
   ## if you want to kill or stop the server processes 
    kill -9 861       "861 is a PID of the running port server"
    
    
   ##  if you want to run todo-app with the help of docker to install docker
   sudo apt install docker.io
   create Dockerfile
   vi Dockerfile
   
      FROM python:3
      RUN pip install django==3.2
      COPY . .
      RUN python manage.py migrate
      CMD ["python","manage.py","runserver","0.0.0.0:8001"]

   ## build the dockerfile
   docker build . -t todo-app
   
   sudo docker run -p 8001:8001 <IMAGE ID>    
   sudo docker run -d -p 8001:8001 <IMAGE ID>    "" in backgrounds and""
   
   ### Jenkins Installetion 
   #for jenkins firstly you need java so 
    sudo apt update
    sudo apt install openjdk-11-jre -y

#Jenkins
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y

#for start jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
 
 go to web and use  public IP:8080        ""you found jenkins page""
 
 ## for jenkins passward use
 sudo cat /var/lib/jenkins/secrets/initialAdminPassword
 
 
 
 
 
