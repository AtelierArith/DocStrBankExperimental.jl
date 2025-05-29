```
@log [logger] args...
```

Logs the data with `logger`, which is the default logger if not provided. Can be any of the following forms:

```
@log "name" 1.0    # literal value
@log "name" 2a     # an expression
@log "name" name   # a variable
@log name          # shortcut for previous
```

If the specified entry is active at the current verbosity level, 
