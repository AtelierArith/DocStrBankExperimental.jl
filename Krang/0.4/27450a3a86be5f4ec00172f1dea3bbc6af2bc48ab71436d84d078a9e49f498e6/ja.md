```julia
get_radial_roots(
    metric::Krang.Kerr{T},
    η,
    λ
) -> NTuple{4, Any}

```

$$
r^4 + (a^2-η-λ^2)r^2 + 2(η+(a-λ)^2)r - a^2η
$$

の根を返します

# 引数

  * `metric`: Kerr{T} メトリック
  * `η`  : 縮小されたカーター定数
  * `λ`  : 縮小された方位角運動量
