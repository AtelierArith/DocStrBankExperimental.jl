```
@cron(expression::String, func::Function)
```

Registers a function with a cron expression. This will extract either the function name or the random Id julia assigns to each lambda function.
