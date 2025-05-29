```
quaternion(θ, n::Vec; normalize = true)
```

角度 `θ` と軸 `n` から `Quaternion` を構築します。

$$
q = \cos\frac{\theta}{2} + \bm{n} \sin\frac{\theta}{2}
$$

構築されたクォータニオンは、デフォルトで `norm(q) ≈ 1` となるように正規化されています。

# 例

```jldoctest
julia> q = quaternion(π/4, Vec(0,0,1))
0.9238795325112867 + 0.0𝙞 + 0.0𝙟 + 0.3826834323650898𝙠

julia> x = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> (q * x / q).vector ≈ rotmatz(π/4) * x
true
```
