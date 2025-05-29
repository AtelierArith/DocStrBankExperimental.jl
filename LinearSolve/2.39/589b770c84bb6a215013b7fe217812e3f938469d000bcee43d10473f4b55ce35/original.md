```julia
PanuaPardisoIterate(; nprocs::Union{Int, Nothing} = nothing,
    matrix_type = nothing,
    iparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    dparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing)
```

A mixed factorization+iterative method using Panua Pardiso.

!!! note
    Using this solver requires adding the package Pardiso.jl, i.e. `using Pardiso`


## Keyword Arguments

For the definition of the keyword arguments, see the Pardiso.jl documentation. All values default to `nothing` and the solver internally determines the values given the input types, and these keyword arguments are only for overriding the default handling process. This should not be required by most users.
