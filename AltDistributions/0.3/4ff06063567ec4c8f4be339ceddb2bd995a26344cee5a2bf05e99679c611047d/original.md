```julia
logpdf_C(d, L)

```

Calculate logdpf + constant for the LKJL distribution for a Cholesky factor of a correlation matrix. Note that

1. `L` is not checked to be a valid Cholesky factor of a correlation matrix,
2. the constant is not calculated, to speed up computation –- the intended usage is MCMC

sampling.
