```
cheb_lobatto_barycentric_weights([TF=Float64], n::Integer) where {TF<:AbstractFloat}
```

2次のチェビシェフ点のためのバリセントリック重みを計算します。

# 引数

  * `TF`: 重みの型パラメータ（例：Float64）
  * `n`: 点の数

# 参考文献

  * [chebfun/@chebtech2/barywts.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech2/barywts.m)

関連項目: [`BarycentricInterpolation`](@ref)
