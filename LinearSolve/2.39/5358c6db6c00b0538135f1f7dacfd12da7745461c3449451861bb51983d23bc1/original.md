```julia
PardisoJL(; nprocs::Union{Int, Nothing} = nothing,
    solver_type = nothing,
    matrix_type = nothing,
    iparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    dparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    vendor::Union{Symbol, Nothing} = nothing
)
```

A generic method using  Pardiso. Specifying `solver_type` is required.

!!! note
    Using this solver requires adding the package Pardiso.jl, i.e. `using Pardiso`


## Keyword Arguments

The `vendor` keyword allows to choose between Panua pardiso  (former pardiso-project.org; `vendor=:Panua`) and  MKL Pardiso (`vendor=:MKL`). If `vendor==nothing`, Panua pardiso is preferred over MKL Pardiso.

For the definition of the other keyword arguments, see the Pardiso.jl documentation. All values default to `nothing` and the solver internally determines the values given the input types, and these keyword arguments are only for overriding the default handling process. This should not be required by most users.
