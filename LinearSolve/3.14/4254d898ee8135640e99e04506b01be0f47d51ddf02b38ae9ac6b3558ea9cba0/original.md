```julia
AppleAccelerateLUFactorization()
```

A wrapper over Apple's Accelerate Library. Direct calls to Acceelrate in a way that pre-allocates workspace to avoid allocations and does not require libblastrampoline.
