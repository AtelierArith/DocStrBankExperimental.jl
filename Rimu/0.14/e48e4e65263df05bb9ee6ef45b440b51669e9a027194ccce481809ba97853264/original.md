```
smart_logger(args...)
```

Enable terminal progress bar during interactive use (i.e. unless running on CI or HPC). Arguments are passed on to the logger. This is run once during `Rimu` startup. Undo with [`default_logger`](@ref) or by setting `Base.global_logger()`.
