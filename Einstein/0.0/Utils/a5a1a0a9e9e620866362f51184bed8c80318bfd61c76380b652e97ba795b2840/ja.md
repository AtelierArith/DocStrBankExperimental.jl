```
BarycentricInterpolation{TF<:AbstractFloat}(points::AbstractVector{TF}, weights::AbstractVector{TF})
```

事前に計算された重みを持つバリセントリック補間を表す構造体。

# フィールド

  * `points::AbstractVector{TF}`: 補間点のベクトル（通常はチェビシェフ点）
  * `weights::AbstractVector{TF}`: バリセントリック重みのベクトル

# メソッド

```
(itp::BarycentricInterpolation{TF})(values::AbstractVector{TFC}, x::TF) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}}
```

関数値のために点 `x` で補間関数を評価します。

# 参考文献

  * [chebfun/@chebtech2/bary.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech2/bary.m)
  * [Berrut2004](@citet*)
