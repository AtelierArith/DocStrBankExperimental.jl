```
log_property!(logger, system, neighbors=nothing, step_n=0;
              n_threads=Threads.nthreads(), kwargs...)
```

Log a property of a system throughout a simulation.

Custom loggers should implement this function. Additional keyword arguments can be passed to the logger if required.
