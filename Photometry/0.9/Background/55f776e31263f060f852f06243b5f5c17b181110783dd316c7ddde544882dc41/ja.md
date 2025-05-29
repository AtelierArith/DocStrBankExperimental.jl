```
BiweightLocationBackground(c = 6.0, M = nothing)
```

ロバストバイウェイト位置統計量を使用して背景を推定します。

$$
ξ_{biloc} = M + \frac{∑_{|uᵢ|<1}{(xᵢ - M)(1 - uᵢ²)²}}{∑_{|uᵢ|<1}{(1-uᵢ²)²}}
$$

$$
u_i = \frac{(x_i - M)}{c⋅\mathrm{MAD}(x)}
$$

ここで、$\mathrm{MAD}(x)$は`x`の中央値絶対偏差です。

# 例

```jldoctest
julia> x = ones(3,5);

julia> BiweightLocationBackground()(x)
1.0

julia> BiweightLocationBackground(c=5.5)(x; dims = 1)
1×5 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0
```
