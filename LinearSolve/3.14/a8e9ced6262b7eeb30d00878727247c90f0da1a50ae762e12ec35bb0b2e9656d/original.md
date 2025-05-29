```julia
MetalLUFactorization()
```

A wrapper over Apple's Metal GPU library. Direct calls to Metal in a way that pre-allocates workspace to avoid allocations and automatically offloads to the GPU.
