```
PositivityPreservingLimiterShallowWater(; variables)
```

リミッターは浅水方程式専用に設計されています。これは、方程式構造体から定義された `threshold_limiter` を使用して、与えられた順序で全てのスカラー `variables` に適用され、最小限の許容値を決定します。`variables` の順序は重要であり、堅牢性に強い影響を与える可能性があります。このリミッターは、[`ShallowWaterEquationsWetDry1D`](@ref)、[`ShallowWaterEquationsWetDry2D`](@ref)、および [`ShallowWaterMultiLayerEquations1D`](@ref) に利用可能です。

標準版の [`Trixi.PositivityPreservingLimiterZhangShu`](@extref) と異なり、水位が `threshold_limiter` 未満のノードは特別な方法で扱われます。ゼロに近い速度によって引き起こされる数値的問題を避けるために、速度はカットオフされ、ノードは「乾燥」として識別されることができます。ここで使用される `ShallowWaterEquationsWetDry` の特別な特徴は、底の地形が解ベクトル `u` に追加の量として保存されることです。しかし、底の地形の値は変更されるべきではありません。そのため、制限されません。

制限プロセスが全ての自由度に適用された後、安全上の理由から、`threshold_limiter` が全てのDGノードに再度適用され、水位が下回らないようにします。セルの平均値がリミッターを適用する前に閾値を下回っている場合、リミッターの論理により、その後に乾燥ノードが存在する可能性があります。さらに、乾燥状態近くの数値的問題を避けるために、制限後に速度のデシンギュラリゼーションが適用されます。デシンギュラリゼーション戦略の詳細は、論文のセクション2.2に記載されています。

  * A. Kurganov, G. Petrova (2007) A second-order well-balanced positivity preserving central-upwind scheme for the Saint-Venant system [doi: 10.4310/CMS.2007.v5.n1.a6](https://dx.doi.org/10.4310/CMS.2007.v5.n1.a6)

[`ShallowWaterMultiLayerEquations1D`](@ref) の実装は異なります。この場合、ポジティビティリミッターは層ごとに適用され、各層内で水位 `h` のみが制限されます。

この完全離散ポジティビティ保持リミッターは、以下の研究に基づいています。

  * Zhang, Shu (2011) Maximum-principle-satisfying and positivity-preserving high-order schemes for conservation laws: survey and new developments [doi: 10.1098/rspa.2011.0153](https://doi.org/10.1098/rspa.2011.0153)

[`ShallowWaterMultiLayerEquations1D`](@ref) の特定の実装は、以下の研究に基づいています。

  * Y. Xing, X. Zhang (2013) Positivity-preserving well-balanced discontinuous Galerkin methods for the shallow water equations on unstructured triangular meshes [doi: 10.1007/s10915-012-9644-4](https://doi.org/10.1007/s10915-012-9644-4)

```
