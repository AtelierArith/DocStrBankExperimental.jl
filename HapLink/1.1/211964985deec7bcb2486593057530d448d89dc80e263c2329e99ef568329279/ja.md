```
VariationCall
```

`Variation`を表し、十分なメタデータを持つ整列リードによってその有効性を支持または反証することができます。これは、[Variant Call Format](https://github.com/samtools/hts-specs#variant-calling-data-files)の行に変換されるか、[`VCF.Record`](https://rasmushenningsson.github.io/VariantCallFormat.jl/stable/vcf-bcf/)に変換されるように設計されています。

# フィールド

  * `variation::Variation`: このコールの`Variation`
  * `quality::Union{Nothing,Number}`: `variation`のベースコールのPhred品質
  * `filter::Vector{String}`: `variation`がフィルターを通過したか、実際にバリアントコールであるか、またはそれに失敗した基準のリスト
  * `depth::Union{Nothing,UInt}`: `leftposition(variation)`をカバーするリードの数
  * `strandbias::Union{Nothing,Float64}`: `variation`が正のストランドに現れる割合
  * `altdepth::Union{Nothing,UInt}`: `variation`が発生するタイプの数
  * `readpos::Union{Nothing,UInt}`: 各リードにおける`variation`の平均相対位置
  * `pvalue::Union{Nothing,Float64}`: このコールのフィッシャーの正確検定の$p$-値
