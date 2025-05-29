```
plan_laplacian!(dims::Tuple,[with_inverse=false],[fftw_flags=FFTW.ESTIMATE],
                      [factor=1.0][,nthreads=length(Sys.cpu_info())])
```

Same as [`plan_laplacian`](@ref), but operates in-place on data. The number of threads `threads` defaults to the number of logical CPU cores on the system.
