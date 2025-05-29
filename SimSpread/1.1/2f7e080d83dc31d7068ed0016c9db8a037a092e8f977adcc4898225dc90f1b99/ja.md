```
predict(I::Tuple{T,T}, ytest::T; GPU::Bool=false) where {T<:NamedMatrix}
```

クエリノードとターゲットノード間の相互作用を、Wuら（2016）によって提案された*de novo*ネットワークベースの推論モデルを使用して予測します。

# 引数

  * `I::Tuple{NamedMatrix,NamedMatrix}`: 特徴源ターゲット三層隣接行列
  * `ytest::NamedMatrix`: クエリターゲット二部隣接行列
  * `GPU::Bool`: 計算のためにGPUアクセラレーションを使用する（デフォルト = false）

# 参考文献

1. Wu, et al (2016). SDTNBI: an integrated network and chemoinformatics tool for systematic prediction of drug–target interactions and drug repositioning. Briefings in Bioinformatics, bbw012. https://doi.org/10.1093/bib/bbw012
2. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
