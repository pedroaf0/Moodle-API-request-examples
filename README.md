# Moodle API request examples by @pedroaf0

# Get start


## Login



`GET or POST /login/token.php?username=<username>&password=<pass>&service=moodle_mobile_app`

| Parameter     | Description   | type  |
| ------------- |:-------------:| -----:|
| Username      | Username for login | string |
| Password      | Login password      |   string |
| Service | Service asking for login. Usually `moodle_mobile_app` is used for moodle without modifications      |    string |


    curl -i -H 'Accept: application/json' http://localhost/login/token.php?username=<username>&password=<pass>&service=moodle_mobile_app

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    {
    "token": "f761c6b41511123456k93ec8f249a3e2",
    "privatetoken": "GvsO51GIfYrIbj12345678CHEe9O6DLcOEqTd7RL7qd5FVLydkRRD6W3qldrpl"
    }

### Error

    HTTP/1.1 500 internal server error
    Status: 500 internal server error
    Connection: close
    Content-Type: application/json

    {
      "error": "Wrong username or password. Please try again.",
      "errorcode": "invalidlogin",
      "stacktrace": null,
      "debuginfo": null,
      "reproductionlink": null
    }
    
    
 

## Get site info



`GET or POST /webservice/rest/server.php?moodlewsrestformat=json&wsfunction=core_webservice_get_site_info&moodlewssettingfilter=true&moodlewssettingfileurl=true&wstoken=<wstoken>`

| Parameter     | Description   | type  |
| ------------- |:-------------:| -----:|
| Wstoken      | User token geted at login | string |
| Moodlewsrestformat      | Response format can be `json` or `xml`        |   string |
| Wsfunction | Requested function a list of all functions can be seen [here](https://docs.moodle.org/dev/Web_service_API_functions)    |    string |


    curl -i -H 'Accept: application/json' http://localhost/webservice/rest/server.php?moodlewsrestformat=json&wsfunction=core_webservice_get_site_info&moodlewssettingfilter=true&moodlewssettingfileurl=true&wstoken=0761c6b415116da123458f249a3e2

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    {
      "sitename": "IFRS - Campus Sertão",
      "username": "2019309735",
      "firstname": "Pedro",
      "lastname": "Afonso Machado Nunes",
      "fullname": "Pedro Afonso Machado Nunes",
      "lang": "pt_br",
      "userid": 480,
      "siteurl": "https:\/\/moodle.sertao.ifrs.edu.br",
      "userpictureurl": "https:\/\/moodle.sertao.ifrs.edu.br\/pluginfile.php\/3816\/user\/icon\/moove\/f1?rev=360545",
      "functions": [...],
      "downloadfiles": 1,
      "uploadfiles": 1,
      "release": "3.9.3+ (Build: 20201224)",
      "version": "2020061503.07",
      "mobilecssurl": "",
      "advancedfeatures": [...],
      "usercanmanageownfiles": true,
      "userquota": 524288000,
      "usermaxuploadfilesize": 10485760,
      "userhomepage": 1,
      "userprivateaccesskey": "e45ea3d9cd53mc123459Sfb2a",
      "siteid": 1,
      "sitecalendartype": "gregorian",
      "usercalendartype": "gregorian",
      "userissiteadmin": false,
      "theme": "moove"
    }

### Error

    HTTP/1.1 500 internal server error
    Status: 500 internal server error
    Connection: close
    Content-Type: application/json

    {
      "exception": "moodle_exception",
      "errorcode": "invalidtoken",
      "message": "Token inválido - token não encontrado"
    }
    
 
