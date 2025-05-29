```
rand(x :: pbox, n :: Int64)
```

は、pbox x から n 個のランダムな区間を返します。

# 例

```jldoctest
julia> a = N(0,1);

julia> rand(a,5)
5-element Vector{Interval{Float64}}:
  [0.538836, 0.553385]
 [-0.331854, -0.318639]
  [0.125661, 0.138305]
 [-1.40508, -1.3722]
 [-0.31864, -0.30548]
```

参照: [`cut`](@ref), [`cdf`](@ref), [`mass`](@ref)
