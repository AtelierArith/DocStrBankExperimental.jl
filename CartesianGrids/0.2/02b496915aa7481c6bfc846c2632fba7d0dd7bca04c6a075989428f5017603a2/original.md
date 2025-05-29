```
plan_intfact!(a::Real,dims::Tuple,[fftw_flags=FFTW.ESTIMATE][,nthreads=length(Sys.cpu_info())])
```

Same as [`plan_intfact`](@ref), but the resulting operator performs an in-place operation on data. The number of threads `threads` defaults to the number of logical CPU cores on the system.
