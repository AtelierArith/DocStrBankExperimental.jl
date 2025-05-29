```
function iscorrectcontroller(client::AuraControlClient)
```

Check if the client's controller number matches the server's controller number. It is not actually necessary these two match, but checking this may help avoid sending commands to the wrong controller.
