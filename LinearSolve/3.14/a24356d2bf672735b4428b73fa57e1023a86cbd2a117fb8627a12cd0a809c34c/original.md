```julia
MKLLUFactorization()
```

A wrapper over Intel's Math Kernel Library (MKL). Direct calls to MKL in a way that pre-allocates workspace to avoid allocations and does not require libblastrampoline.
