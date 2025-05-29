```
TransformedDIDResult{TR,P,M} <: AbstractDIDResult{TR}
```

すべての係数推定値の線形変換から得られた推定結果 [`DIDResult`](@ref) から。さらに [`TransSubDIDResult`](@ref)、[`lincom`](@ref) および [`rescale`](@ref) も参照してください。

# パラメータ

  * `P`: 変換された結果の型。
  * `M`: 線形変換を表す行列の型。
