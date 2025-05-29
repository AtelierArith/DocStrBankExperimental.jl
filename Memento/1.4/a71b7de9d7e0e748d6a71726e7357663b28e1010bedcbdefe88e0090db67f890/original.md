```
setlevel!(f::Function, logger::Logger, level::AbstractString; recursive=false)
```

Temporarily change the level a logger will log at for the duration of the function `f`.
