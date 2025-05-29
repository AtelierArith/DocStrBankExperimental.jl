```
Tables.table(m::AbstractVecOrMat; [header])
```

Wrap an `AbstractVecOrMat` (`Matrix`, `Vector`, `Adjoint`, etc.) in a `MatrixTable`, which satisfies the Tables.jl interface.  (An `AbstractVector` is treated as a 1-column matrix.) This allows accessing the matrix via `Tables.rows` and `Tables.columns`. An optional keyword argument iterator `header` can be passed which will be converted to a `Vector{Symbol}` to be used as the column names. Note that no copy of the `AbstractVecOrMat` is made.
