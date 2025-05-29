```
tee(c::OutputCollector; colored::Bool = false, stream::IO = stdout)
```

Spawn a background task to incrementally output lines from `collector` to the standard output, optionally colored.
