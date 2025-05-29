```
test_cputime(nx,ny,nthreads_max;[nsamp=1][,testtype=:laplacian][,kwargs]) -> Float64, Float64
```

Evaluate a sample FFT-based problem with the given size of grid `nx` x `ny` and the provided maximum number of threads `nthreads_max`. Returns the mean and standard deviation of the computational time. The optional argument `nsamp` can be used to perform an average timing over multiple samples. The test type is specified with the `testtype` optional argument. The default test is inversion of a Laplacian (`:laplacian`). Other options are `:intfact` and `:helmholtz`.
