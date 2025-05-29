```
StateSpaceSet{D, T, V} <: AbstractVector{V}
```

A dedicated interface for sets in a state space. It is an **ordered container of equally-sized points** of length `D`, with element type `T`, represented by a vector of type `V`. Typically `V` is `SVector{D,T}` or `Vector{T}` and the data are always stored internally as `Vector{V}`. `SSSet` is an alias for `StateSpaceSet`.

The underlying `Vector{V}` can be obtained by `vec(ssset)`, although this is almost never necessary because `StateSpaceSet` subtypes `AbstractVector` and extends its interface. `StateSpaceSet` also supports almost all sensible vector operations like `append!, push!, hcat, eachrow`, among others. When iterated over, it iterates over its contained points.

## Construction

Constructing a `StateSpaceSet` is done in three ways:

1. By giving in each individual **columns** of the state space set as `Vector{<:Real}`: `StateSpaceSet(x, y, z, ...)`.
2. By giving in a matrix whose rows are the state space points: `StateSpaceSet(m)`.
3. By giving in directly a vector of vectors (state space points): `StateSpaceSet(v_of_v)`.

All constructors allow for the keyword `container` which sets the type of `V` (the type of inner vectors). At the moment options are only `SVector`, `MVector`, or `Vector`, and by default `SVector` is used.

## Description of indexing

When indexed with 1 index, `StateSpaceSet` behaves exactly like its encapsulated vector. i.e., a vector of vectors (state space points). When indexed with 2 indices it behaves like a matrix where each row is a point.

In the following let `i, j` be integers, `typeof(X) <: AbstractStateSpaceSet` and `v1, v2` be `<: AbstractVector{Int}` (`v1, v2` could also be ranges, and for performance benefits make `v2` an `SVector{Int}`).

  * `X[i] == X[i, :]` gives the `i`th point (returns an `SVector`)
  * `X[v1] == X[v1, :]`, returns a `StateSpaceSet` with the points in those indices.
  * `X[:, j]` gives the `j`th variable timeseries (or collection), as `Vector`
  * `X[v1, v2], X[:, v2]` returns a `StateSpaceSet` with the appropriate entries (first indices being "time"/point index, while second being variables)
  * `X[i, j]` value of the `j`th variable, at the `i`th timepoint

Use `Matrix(ssset)` or `StateSpaceSet(matrix)` to convert. It is assumed that each *column* of the `matrix` is one variable. If you have various timeseries vectors `x, y, z, ...` pass them like `StateSpaceSet(x, y, z, ...)`. You can use `columns(dataset)` to obtain the reverse, i.e. all columns of the dataset in a tuple.
