```
sum_fast(v::AbstractSmallVector{N,T}) where {N,T}
```

Return the `@fastmath` sum of the elements of `v`. Unlike for `sum`, the return value always is of the element type of `v`, even for small bit integers.

See also `Base.sum`, `Base.@fastmath`.

# Example

```jldoctest
julia> v = SmallVector{4}([-0.0, -0.0])
2-element SmallVector{4, Float64}:
 -0.0
 -0.0

julia> sum(v), sum_fast(v)
(-0.0, 0.0)

julia> v = SmallVector{4}(Int8[80, 90])
2-element SmallVector{4, Int8}:
 80
 90

julia> sum(v), sum_fast(v)
(170, -86)
```
