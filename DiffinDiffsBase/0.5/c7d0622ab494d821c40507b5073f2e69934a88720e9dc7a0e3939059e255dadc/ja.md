```
TransSubDIDResult{TR,P,M,I,TI} <: AbstractDIDResult{TR}
```

線形変換によって得られた推定結果で、[`DIDResult`](@ref)の係数推定値のサブセットから得られます。さらに[`TransformedDIDResult`](@ref)、[`lincom`](@ref)、および[`rescale`](@ref)も参照してください。

# パラメータ

  * `P`: 変換された結果の型。
  * `M`: 線形変換を表す行列の型。
  * `I`: すべての係数のインデックスの型。
  * `TI`: 処置係数のインデックスの型。
