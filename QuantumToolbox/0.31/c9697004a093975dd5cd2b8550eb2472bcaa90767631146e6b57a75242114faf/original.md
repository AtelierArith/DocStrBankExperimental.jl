```
basis(N::Int, j::Int = 0; dims::Union{Int,AbstractVector{Int},Tuple}=N)
```

Generates a fock state like [`fock`](@ref).

It is also possible to specify the list of dimensions `dims` if different subsystems are present.

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `basis(N, j, dims=dims)` with `dims` as a `Tuple` or `SVector` from [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) instead of `Vector`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) about type stability for more details.

