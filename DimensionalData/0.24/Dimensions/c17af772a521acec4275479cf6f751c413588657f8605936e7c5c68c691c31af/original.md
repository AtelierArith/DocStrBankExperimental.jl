```
dims(x, query) => Tuple{Vararg{Dimension}}
dims(x, query...) => Tuple{Vararg{Dimension}}
```

Get the dimension(s) matching the type(s) of the query dimension.

LookupArray can be an Int or an Dimension, or a tuple containing any combination of either.

## Arguments

  * `x`: any object with a `dims` method, or a `Tuple` of `Dimension`.
  * `query`: Tuple or a single `Dimension` or `Dimension` `Type`.

## Example

```jldoctest
julia> using DimensionalData

julia> A = DimArray(ones(2, 3, 2), (X, Y, Z))
2×3×2 DimArray{Float64,3} with dimensions: X, Y, Z
[:, :, 1]
 1.0  1.0  1.0
 1.0  1.0  1.0
[and 1 more slices...]

julia> dims(A, (X, Y))
X, Y

```
