```
activate_multithread(backend::CPU; nthreads=1) = BLAS.set_num_threads(nthreads)
```

Convenience function to set number of BLAS threads. 

# Input arguments

  * `backend` is the only required input which must be `CPU()` from `KernelAbstractions.jl`
  * `nthreads` can be used to set the number of BLAS cores (default `nthreads=1`)
