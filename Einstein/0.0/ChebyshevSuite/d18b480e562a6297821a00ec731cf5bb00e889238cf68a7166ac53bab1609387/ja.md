```
cheb_gauss_barycentric_weights([TF=Float64], n::Integer) where {TF<:AbstractFloat}
```

1種類のチェビシェフ点のためのバリセントリック重みを計算します。

# 引数

  * `TF`: 重みの型パラメータ（デフォルトは Float64）
  * `n`: 点の数

# 参考文献

  * [berrut2004barycentric](@citet*)
  * [chebfun/@chebtech1/barywts.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech1/barywts.m)

関連情報: [`BarycentricInterpolation`](@ref)
