```
barycentric_interpolate(x::TF, points::AbstractVector{TF}, values::AbstractVector{TFC}, weights::Vector{TF}) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}
```

ノード `points`、関数値 `values` およびバリセントリック重み `weights` における点 `x` でのバリセントリック補間公式の値を評価します。

# 参考文献

  * [chebfun/@chebtech2/bary.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech2/bary.m)
  * [Berrut2004](@citet*)
