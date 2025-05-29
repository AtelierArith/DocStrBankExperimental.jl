```
fock(N::Int, j::Int=0; dims::Union{Int,AbstractVector{Int},Tuple}=N, sparse::Union{Bool,Val}=Val(false))
```

Generates a fock state $\ket{\psi}$ of dimension `N`. 

It is also possible to specify the list of dimensions `dims` if different subsystems are present.

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `fock(N, j, dims=dims, sparse=Val(sparse))` instead of `fock(N, j, dims=dims, sparse=sparse)`. Consider also to use `dims` as a `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) instead of `Vector`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

