```
VariationInfo{S<:BioSequence,T<:BioSymbol}
```

整列されたシーケンシングリード内の[`SequenceVariation.Variation`](https://biojulia.dev/SequenceVariation.jl/stable/api/#SequenceVariation.Variation)に関連する統計を表します。

# フィールド

  * `variation::Variation{S,T}`: このオブジェクトが表す`Variation`
  * `readpos::Float64`: シーケンシングリード内で`variation`が発生する位置
  * `quality::Float64`: `variation`のphredスケールのベースコール品質
  * `Strand::GenomicFeatures.Strand`: `variation`が出現するストランド
