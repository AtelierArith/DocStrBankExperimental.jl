```
hasdim([f], x, query::Tuple) => NTUple{Bool}
hasdim([f], x, query...) => NTUple{Bool}
hasdim([f], x, query) => Bool
```

Check if an object `x` has dimensions that match or inherit from the `query` dimensions.

## Arguments

  * `x`: any object with a `dims` method, a `Tuple` of `Dimension` or a single `Dimension`.
  * `query`: Tuple or single `Dimension` or dimension `Type`.
  * `f`: `<:` by default, but can be `>:` to match abstract types to concrete types.

Check if an object or tuple contains an `Dimension`, or a tuple of dimensions.

## Example

```jldoctest
julia> using DimensionalData

julia> A = DimArray(ones(10, 10, 10), (X, Y, Z));

julia> hasdim(A, X)
true

julia> hasdim(A, (Z, X, Y))
(true, true, true)

julia> hasdim(A, Ti)
false
```
