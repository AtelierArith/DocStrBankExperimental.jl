```
rescale_one_zero(𝐱)
rescale_one_zero(x...)
```

`𝐱`の最小値を`1`に、最大値を`0`にマッピングします。

# 例

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
