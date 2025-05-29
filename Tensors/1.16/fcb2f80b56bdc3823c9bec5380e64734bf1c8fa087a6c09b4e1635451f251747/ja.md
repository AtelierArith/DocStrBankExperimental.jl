```
rotate(x::AbstractTensor{2}, θ::Number)
```

2次元テンソル `x` を `θ` ラジアンだけ面外軸の周りに回転させます。

# 例

```jldoctest
julia> x = Vec{2}((0.0, 1.0));

julia> rotate(x, π/4)
2-element Vec{2, Float64}:
 -0.7071067811865475
  0.7071067811865476
```
