```
MatrixTerm{Ts} <: AbstractTerm
```

A collection of terms that should be combined to produce a single numeric matrix.

A matrix term is created by [`apply_schema`](@ref) from a tuple of terms using [`collect_matrix_terms`](@ref), which pulls out all the terms that are matrix terms as determined by the trait function [`is_matrix_term`](@ref), which is true by default for all `AbstractTerm`s.
