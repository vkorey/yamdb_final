# yamdb_final
![yamdb_workflow](https://github.com/vkorey/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Учебный проект YAMDB
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». 
Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).

### Технологии
- Python 3.8.5
- Django 3.0.5
- Nginx
- Gunicorn
- PostgreSQL

### Workflow:
- Тестирование (flake8 и pytest).
- Сборка и публикация на DockerHub.
- Автоматический деплой на удаленный сервер.
- Отправка уведомления в telegram.

### Установка:
1. Склонируйте репозиторий
```
git clone https://github.com/vkorey/yamdb_final
```
2. Подключитесь к вашему удаленному серверу по ssh
3. Установите docker на сервер:
```
sudo apt install docker.io 
```
4. Установите docker-compose на сервер:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
Примените разрешения для исполняемого файла:
```
sudo chmod +x /usr/local/bin/docker-compose
```
4. Отредактируйте файл nginx/default.conf и в строке server_name впишите свой IP
5. Скопируйте файлы docker-compose.yaml и nginx/default.conf из проекта на сервер
6. Добавьте в Secrets GitHub переменные окружения для работы:
```
SECRET_KEY=<secret key django проекта>
DB_ENGINE=django.db.backends.postgresql
DB_HOST=db
DB_NAME=postgres
DB_PASSWORD=postgres
DB_PORT=5432
DB_USER=postgres

DOCKER_PASSWORD=<Docker password>
DOCKER_USERNAME=<Docker username>

USER=<username для подключения к серверу>
HOST=<IP сервера>
PASSPHRASE=<пароль для сервера, если он установлен>
SSH_KEY=<ваш SSH ключ>

TG_CHAT_ID=<ID чата, в который придет сообщение>
TELEGRAM_TOKEN=<токен вашего бота>
```
