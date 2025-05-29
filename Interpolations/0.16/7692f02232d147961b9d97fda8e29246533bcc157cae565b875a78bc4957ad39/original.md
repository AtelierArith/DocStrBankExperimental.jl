```
knotsbetween(iter; start, stop)
knotsbetween(iter, start, stop)
```

Iterate over all knots of `iter` such that `start < k < stop`.

`iter` can be an `AbstractInterpolation`, or the output of `knots` (ie. a `KnotIterator` or `ProductIterator` wrapping `KnotIterator`)

If `start` is not provided, iteration will start from the first knot. An `ArgumentError` will be raised if both `start` and `stop` are not provided.

If no such knots exists will return a KnotIterator with length 0

# Example

```jldoctest
julia> etp = linear_interpolation([1.0, 1.2, 2.3, 3.0], rand(4); extrapolation_bc=Periodic());

julia> knotsbetween(etp; start=38, stop=42) |> collect
6-element Vector{Float64}:
 38.3
 39.0
 39.2
 40.3
 41.0
 41.2
```
