```
KernelFunction{DS,S,DT,T}(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
KernelFunction(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
```

Create a zero-valued Kernel function, i.e. a Kernel function that is zero everywhere. The `codomain` can be a zero-valued domain created via [`Box{DT,T}()`](@ref).

`grid_size` specifies the resolution of the Kernel function. This makes it convenient to use zero-valued Kernel functions as "templates" or "skeletons" when creating other Kernel functions.
