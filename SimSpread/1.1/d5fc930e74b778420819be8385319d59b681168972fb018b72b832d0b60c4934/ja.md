```
validity_ratio(yhat::AbstractVector)
```

有効な予測の比率（スコア > 0）とすべての予測。すべての予測または予測のサブセットに対して予測性能が与えられているかどうかを確認できます。

# 引数

  * `yhat::AbstractVector` : 予測スコア。

# 拡張ヘルプ

SimSpreadの制限の一つは、最初のネットワーク層のすべてのソースに対する類似性が類似性閾値αを下回るクエリノードに対して予測を生成することが不可能であることです。この場合、特徴ベクトルの長さはゼロになり、リソースの拡散は不可能であり、すべてのターゲットに対して予測値はゼロになります。したがって、閾値αの関数として性能を正しく評価するためのガードレールが必要です。

SimSpreadのこの特性は、その適用ドメインの内在的な概念と見なすことができます。意味のないターゲットを返す代わりに、SimSpreadの適用ドメイン外のクエリノードに対してはターゲット予測が生成されません。

# 参考文献

1. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
