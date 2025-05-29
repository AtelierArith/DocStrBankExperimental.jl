```
rotate(x::AbstractTensor{3}, u::Vec{3}, θ::Number)
```

ベクトル `u` の周りに三次元テンソル `x` を合計 `θ` ラジアン回転させます。

# 例

```jldoctest
julia> x = Vec{3}((0.0, 0.0, 1.0));

julia> u = Vec{3}((0.0, 1.0, 0.0));

julia> rotate(x, u, π/2)
3-element Vec{3, Float64}:
 1.0
 0.0
 6.123233995736766e-17
```
