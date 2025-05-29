```
ColVecs(X::AbstractMatrix)
```

A lightweight wrapper for an `AbstractMatrix` which interprets it as a vector-of-vectors, in which each *column* of `X` represents a single vector.

That is, by writing `x = ColVecs(X)`, you are saying "`x` is a vector-of-vectors, each of which has length `size(X, 1)`. The total number of vectors is `size(X, 2)`."

Phrased differently, `ColVecs(X)` says that `X` should be interpreted as a vector of horizontally-concatenated column-vectors, hence the name `ColVecs`.

```jldoctest
julia> X = randn(2, 5);

julia> x = ColVecs(X);

julia> length(x) == 5
true

julia> X[:, 3] == x[3]
true
```

`ColVecs` is related to [`RowVecs`](@ref) via transposition:

```jldoctest
julia> X = randn(2, 5);

julia> ColVecs(X) == RowVecs(X')
true
```
