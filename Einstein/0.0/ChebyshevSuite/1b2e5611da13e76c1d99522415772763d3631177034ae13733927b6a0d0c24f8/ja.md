```
cheb_series_evaluate(coeffs::AbstractVector{TFC}, x::TF) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}
cheb_series_evaluate(coeffs::AbstractVector{TFC}, x::AbstractVector{TF}) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}
```

点でのチェビシェフ係数をクレンショーのアルゴリズムを使用して評価します。

# パフォーマンスノート

  * クレンショーのアルゴリズム: 各点あたりO(n)の操作
  * [TODO] NDCT: 多くの点を同時に処理するためのO(n log n)の操作

# 参考文献

  * [chebfun/@chebtech/clenshaw.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/clenshaw.m)
  * [chebfun/@chebtech/feval.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/feval.m)
