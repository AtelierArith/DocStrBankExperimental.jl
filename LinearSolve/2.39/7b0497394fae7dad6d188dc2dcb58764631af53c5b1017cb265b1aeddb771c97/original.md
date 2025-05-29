```julia
MKLPardisoIterate(; nprocs::Union{Int, Nothing} = nothing,
    matrix_type = nothing,
    cache_analysis = false,
    iparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    dparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing)
```

A mixed factorization+iterative method using MKL Pardiso.

!!! note
    Using this solver requires adding the package Pardiso.jl, i.e. `using Pardiso`


## Keyword Arguments

Setting `cache_analysis = true` disables Pardiso's scaling and matching defaults and caches the result of the initial analysis phase for all further computations with this solver.

For the definition of the other keyword arguments, see the Pardiso.jl documentation. All values default to `nothing` and the solver internally determines the values given the input types, and these keyword arguments are only for overriding the default handling process. This should not be required by most users.
