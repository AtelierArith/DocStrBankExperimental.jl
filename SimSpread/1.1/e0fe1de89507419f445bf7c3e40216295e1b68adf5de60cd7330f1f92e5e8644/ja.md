```
featurize(X::NamedArray, α::AbstractFloat, weighted::Bool=true)
```

特徴行列 `X` を SimSpread 特徴行列に変換します。

# 引数

  * `X::NamedArray`: 連続特徴行列
  * `α::AbstractFloat`: 特徴化カットオフ
  * `weighted::Bool` : 結果に重み付け関数を適用する (デフォルト = true)

# 参考文献

1. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
