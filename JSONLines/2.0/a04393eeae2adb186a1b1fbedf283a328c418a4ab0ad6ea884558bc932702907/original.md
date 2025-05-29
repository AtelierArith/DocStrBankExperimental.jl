```
select(path::String, cols...; nworkers = 1) => LineIndex
```

  * `path`: Path to JSONLines file
  * `cols...`: Columnnames to be selected
  * Keyword Argument:

      * `nworkers=1`: Number of threads to use for operations on the resulting LineIndex
