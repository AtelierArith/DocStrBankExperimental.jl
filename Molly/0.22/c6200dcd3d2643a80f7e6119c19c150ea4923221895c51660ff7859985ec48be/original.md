```
apply_loggers!(system, neighbors=nothing, step_n=0, run_loggers=true;
               n_threads=Threads.nthreads(), kwargs...)
```

Run the loggers associated with a system.

`run_loggers` can be `true`, `false` or `:skipzero`, in which case the loggers are not run before the first step. Additional keyword arguments can be passed to the loggers if required. Ignored for gradient calculation during automatic differentiation.
