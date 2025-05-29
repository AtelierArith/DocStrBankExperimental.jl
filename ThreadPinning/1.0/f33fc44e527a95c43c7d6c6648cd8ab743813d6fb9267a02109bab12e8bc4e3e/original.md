```
openblas_pinthreads(cpuids; nthreads = BLAS.get_num_threads())
```

Pin the OpenBLAS threads to the given CPU IDs. The optional keyword argument `nthreads` serves as a cutoff.
