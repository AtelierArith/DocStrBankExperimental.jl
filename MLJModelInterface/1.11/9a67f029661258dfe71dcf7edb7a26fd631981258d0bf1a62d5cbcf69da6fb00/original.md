```
table(columntable; prototype=nothing)
```

Convert a named tuple of vectors or tuples `columntable`, into a table of the "preferred sink type" of `prototype`. This is often the type of `prototype` itself, when `prototype` is a sink; see the Tables.jl documentation. If `prototype` is not specified, then a named tuple of vectors is returned.

```
table(A::AbstractMatrix; names=nothing, prototype=nothing)
```

Wrap an abstract matrix `A` as a Tables.jl compatible table with the specified column `names` (a tuple of symbols). If `names` are not specified, `names=(:x1, :x2, ..., :xn)` is used, where `n=size(A, 2)`.

If a `prototype` is specified, then the matrix is materialized as a table of the preferred sink type of `prototype`, rather than wrapped. Note that if `prototype` is *not* specified, then `matrix(table(A))` is essentially a no-op.
