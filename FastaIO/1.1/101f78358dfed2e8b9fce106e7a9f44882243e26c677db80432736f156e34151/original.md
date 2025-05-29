```
writefasta([io::IO = stdout], data; check_description=true)
```

This version of the function writes to an already opened `IO` stream, defaulting to `stdout`.

Set the keyword `check_description=false` to disable the warning message given when description lines are too long.
