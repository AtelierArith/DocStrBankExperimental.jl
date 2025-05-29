```
otherdims(x, query) => Tuple{Vararg{Dimension,N}}
```

Get the dimensions of an object *not* in `query`.

## Arguments

  * `x`: any object with a `dims` method, a `Tuple` of `Dimension`.
  * `query`: Tuple or single `Dimension` or dimension `Type`.
  * `f`: `<:` by default, but can be `>:` to match abstract types to concrete types.

A tuple holding the unmatched dimensions is always returned.

## Example

```jldoctest
julia> using DimensionalData, DimensionalData.Dimensions

julia> A = DimArray(ones(10, 10, 10), (X, Y, Z));

julia> otherdims(A, X)
Y, Z

julia> otherdims(A, (Y, Z))
X
```
