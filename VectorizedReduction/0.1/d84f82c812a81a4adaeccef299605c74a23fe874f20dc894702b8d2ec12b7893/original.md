```
vtextrema([f=identity], A::AbstractArray; [dims=:], [init=(mn,mx)])
```

Compute the minimum and maximum values by calling `f` on each element of of `A` over the given `dims`, with the `mn` and `mn` initialized by the respective arguments of the 2-tuple `init`, which can be any combination of values (`<:Number`) or functions which accept a single type argument. Threaded.

# Warning

`NaN` values are not handled!

# Examples

```jldoctest
julia> A = reshape(Vector(1:2:16), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  5
 3  7

[:, :, 2] =
  9  13
 11  15

julia> vtextrema(abs2, A, dims=(1,2), init=(typemax, 100))
1×1×2 Array{Tuple{Int64, Int64}, 3}:
[:, :, 1] =
 (1, 100)

[:, :, 2] =
 (81, 225)

julia> vtextrema(abs2, A, init=(typemax, 100))
(1, 225)
```
