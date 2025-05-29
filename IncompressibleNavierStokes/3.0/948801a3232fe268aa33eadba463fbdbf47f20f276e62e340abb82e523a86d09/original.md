```julia
pad_scalarfield_mat(setup) -> Any

```

Create matrix for padding inner scalar field with boundary volumes. This can be useful for algorithms that require vectors with degrees of freedom only, and not the ghost volumes. To go back, simply transpose the matrix.

See also: [`pad_vectorfield_mat`](@ref).
