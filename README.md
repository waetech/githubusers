# githubusers
This project is about loading Github Users using AJAX and Javascript into a simple web page.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Ajax 3 - External Users</title>
    <style>
    .user{
        display: flex; 
        background:#f4f4f4;
        padding:10px;
        margin-bottom:10px;
    }

    .user ul{
        list-style:none;
    }
    </style>
</head>
<body>
    <button id="btn">Load Github Users</button>
    <br><br>
    <div id="users"></div>
    

<script>
    document.getElementById('btn').addEventListener('click', loadUsers);

function loadUsers(){
    var xhr = new XMLHttpRequest();
    xhr.open('GET', 'https://api.github.com/users', true);

    xhr.onload = function(){
        //check for status
        if(this.status === 200){
            var users = JSON.parse(this.responseText);

            //console.log(users);
            
            var output = ' ';
            for(var i in users){
                output +=
                '<div class="user>'+
            '<img src="'+users[i].avatar_url+'" width="70" height="70">' +
            '<ul>' +
            '<li>ID: '+users[i].id+ '</li>'+
            '<li>Login: '+users[i].login+ '</li>'+
            '</ul>'+
            '</div>';
            }

            document.getElementById('users').innerHTML = output;
            


        }
    }
    xhr.send();
}    
               

  
    

           
        

      
    
</script>
</body>
</html>
