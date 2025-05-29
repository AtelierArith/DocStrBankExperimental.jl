```
IsStochasticWithThreshold{T=Float64}(threshold=1.0) <: StochasticStyle{T}
```

浮動小数点ウォーカーナンバーを使用した確率的伝播。ベクトル行列積の間、各個別の対角線および生成結果は、`threshold`より小さい場合に確率的に丸められます（消滅の前に）。よりカスタマイズ可能な確率的スタイルについては、[`IsDynamicSemistochastic`](@ref)を参照してください。

また、[`StochasticStyle`](@ref)も参照してください。
