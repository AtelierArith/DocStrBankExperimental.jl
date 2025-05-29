```
struct ErrorLogger <: Logger
ErrorLogger(nof_eigvals=100,nof_iters=100,displaylevel=1)
```

Use this object if you want to save the error history in a method. The `displaylevel` is interpreted as in `PrintLogger`. The kwargs `nof_eigvals` and `nof_iters` is used to preallocate memory used for saving.

When you use this logger, the error of `push_iteration_info!`-calls will be stored in `logger.errs`.
