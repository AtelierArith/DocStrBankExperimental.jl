```
@cron(expression::String, name::String, func::Function)
```

This variation provides way manually "name" a registered function. This information is used by the server on startup to log out all cron jobs.
