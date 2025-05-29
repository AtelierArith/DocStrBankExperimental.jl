```
cheb_series_derivative!(coeffs::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
cheb_series_derivative!(coeffs_der::AbstractVector{TFC}, coeffs::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
cheb_series_derivative(coeffs::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
```

チェビシェフ級数の係数の導関数を計算します。

# 引数

  * `coeffs`: 長さ n のチェビシェフ係数の入力ベクトル

# 参考文献

  * [chebfun/@chebtech/diff.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/diff.m)
