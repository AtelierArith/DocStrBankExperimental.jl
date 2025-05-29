```
rescale_one_zero(𝐱)
rescale_one_zero(x...)
```

Map the minimum of `𝐱` to `1` and the maximum to `0`.

# Examples

```jldoctest
julia> 𝐱 = [2.0, 4.0, 6.0];

julia> s = rescale_one_zero(𝐱)
y = -0.25 x + 1.5

julia> s.(𝐱)
3-element Vector{Float64}:
 1.0
 0.5
 0.0
```
