```
fock_dm(N::Int, j::Int=0; dims::Union{Int,AbstractVector{Int},Tuple}=N, sparse::Union{Bool,Val}=Val(false))
```

Density matrix representation of a Fock state.

Constructed via outer product of [`fock`](@ref).

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `fock_dm(N, j, dims=dims, sparse=Val(sparse))` instead of `fock_dm(N, j, dims=dims, sparse=sparse)`. Consider also to use `dims` as a `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) instead of `Vector`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

