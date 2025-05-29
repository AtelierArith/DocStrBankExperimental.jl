```
rescale_zero_one(𝐱)
rescale_zero_one(x...)
```

Map the minimum of `𝐱` to `0` and the maximum to `1`.

# Examples

```jldoctest
julia> 𝐱 = [2.0, 4.0, 6.0];

julia> s = rescale_zero_one(𝐱)
y = 0.25 x - 0.5

julia> s.(𝐱)
3-element Vector{Float64}:
 0.0
 0.5
 1.0
```
