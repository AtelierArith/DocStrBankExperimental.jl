```
dimnum(x, query::Tuple) => NTuple{Int}
dimnum(x, query) => Int
```

Get the number(s) of `Dimension`(s) as ordered in the dimensions of an object.

## Arguments

  * `x`: any object with a `dims` method, a `Tuple` of `Dimension` or a single `Dimension`.
  * `query`: Tuple, Array or single `Dimension` or dimension `Type`.

The return type will be a Tuple of `Int` or a single `Int`, depending on wether `query` is a `Tuple` or single `Dimension`.

## Example

```jldoctest
julia> using DimensionalData

julia> A = DimArray(ones(10, 10, 10), (X, Y, Z));

julia> dimnum(A, (Z, X, Y))
(3, 1, 2)

julia> dimnum(A, Y)
2
```
