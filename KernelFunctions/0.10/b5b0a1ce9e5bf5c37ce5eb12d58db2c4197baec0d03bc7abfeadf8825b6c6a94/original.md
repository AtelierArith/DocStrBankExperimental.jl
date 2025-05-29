```
TransformedKernel(k::Kernel, t::Transform)
```

Kernel derived from `k` for which inputs are transformed via a [`Transform`](@ref) `t`.

The preferred way to create kernels with input transformations is to use the composition operator [`∘`](@ref) or its alias `compose` instead of `TransformedKernel` directly since this allows optimized implementations for specific kernels and transformations.

See also: [`∘`](@ref)
