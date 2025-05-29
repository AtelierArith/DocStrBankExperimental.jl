```
E=exponential!(A,[method [cache]])
```

Computes the matrix exponential with the method specified in `method`. The contents of `A` are modified, allowing for fewer allocations. The `method` parameter specifies the implementation and implementation parameters, e.g. [`ExpMethodNative`](@ref), [`ExpMethodDiagonalization`](@ref), [`ExpMethodGeneric`](@ref), [`ExpMethodHigham2005`](@ref). Memory needed can be preallocated and provided in the parameter `cache` such that the memory can be recycled when calling `exponential!` several times. The preallocation is done with the command [`alloc_mem`](@ref): `cache=alloc_mem(A,method)`. `A` may not be sparse matrix type, since exp(A) is likely to be dense.

Example

```julia-repl
julia> A = randn(50, 50);

julia> B = A * 2;

julia> method = ExpMethodHigham2005();

julia> cache = ExponentialUtilities.alloc_mem(A, method); # Main allocation done here

julia> E1 = exponential!(A, method, cache) # Very little allocation here

julia> E2 = exponential!(B, method, cache) # Very little allocation here

```
