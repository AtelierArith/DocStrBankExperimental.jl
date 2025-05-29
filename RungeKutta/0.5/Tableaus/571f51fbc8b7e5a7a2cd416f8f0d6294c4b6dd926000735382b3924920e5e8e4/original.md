```julia
get_lobatto_nullvector(::Type, s; normalize=false)
get_lobatto_nullvector(s; kwargs...)
```

Computes the nullvector of the matrix containing the derivatives of the Lagrange basis on the `s` Lobatto nodes evaluated on these nodes.
