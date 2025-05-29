```
map2parametric(
    self::ET,
    x::Matrix{FT},
    pt::Vector{FT};
    tolerance = 0.001,
    maxiter = 5,
) where {ET<:AbstractFESet, FT}
```

空間位置をパラメトリック座標にマップします。

  * `x`=ノードの空間座標の配列、size(x) = nbfuns x dim,
  * `c`= 空間位置
  * `tolerance` = パラメトリック座標の許容誤差; デフォルトは 0.001。

# 戻り値

  * `success` = ブールフラグ、成功した場合は true、そうでない場合は false。
  * `pc` = 解が成功した場合はパラメトリック座標の行配列を返し、そうでない場合は NaN が返されます。
