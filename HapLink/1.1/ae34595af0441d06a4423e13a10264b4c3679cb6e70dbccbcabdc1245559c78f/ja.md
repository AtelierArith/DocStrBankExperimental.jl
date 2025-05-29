```
HaplotypeCall{S,T}
```

リンク不均衡計算が行われ、妥当性を確認または否定するためのメタデータを持つ`Haplotype`。`Haplotype`に対する[`VariationCall`](@ref)に非常に似ています。

# フィールド

  * `depth::UInt64`: `haplotype`内のすべての`Variation`を含むシーケンシングリードの数
  * `linkage::Float64`: このコールの非加重リンク不均衡係数
  * `frequency::Float64`: このハプロタイプが全リードプールに対してどのくらいの頻度で発生するか
  * `significance::Float64`: このコールの$χ^2$統計的有意性（$p$-値）
  * `haplotype::Haplotype{S,T}`: このコールで一緒に継承される`Variation`のセット
