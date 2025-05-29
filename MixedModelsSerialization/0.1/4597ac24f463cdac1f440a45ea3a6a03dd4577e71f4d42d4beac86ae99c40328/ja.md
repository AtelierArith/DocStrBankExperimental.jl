```
MixedModelSummary{T} <: MixedModel{T}
MixedModelSummary(m::LinearMixedModel)
```

`MixedModel`の「サマリー」のための抽象型で、メモリフットプリントが削減されています。

具体的なサブタイプは、`MixedModel`のモデル行列を持たないため、特に多くの観測値を持つモデルに対しては、はるかに少ないメモリを消費します。ただし、元のデータに依存しない一般的な`StatsAPI`メソッドを実装するために、関連するパラメータや導出値を格納することがあります。

詳細は[`LinearMixedModelSummary`](@ref)を参照してください。
