```julia
mass_matrix(state)

```

Calculate the mass matrix for use with [`SciMLBase.ODEFunction`](@ref). Return a Diagonal matrix if it occurs to be diagonal, otherwise return a SparseMatrixCSC.
