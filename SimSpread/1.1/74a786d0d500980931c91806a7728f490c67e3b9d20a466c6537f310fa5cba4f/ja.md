```
spread(G::AbstractMatrix{Float64})
```

トリレイヤー特徴-ソース-ターゲットネットワークの隣接行列に対する転送行列を計算します。

# 引数

  * `G::AbstractMatrix{Float64}`: トリレイヤー特徴-ソース-ターゲットネットワークの隣接行列。

# 拡張ヘルプ

グラフ内のノード間の潜在的な相互作用は、特徴-ソース-ターゲットネットワーク、すなわち前述のグラフ `G` におけるリソース拡散プロセスを使用することで特定できます。ネットワーク内の各ノード nᵢ は、隣接ノードとその特徴に初期リソースを持っています。最初に、各特徴と nᵢ の各隣接ノードは、そのリソースを隣接ノードに均等に分配します。その後、これらのノードはそれぞれ隣接ノードにリソースを均等に分配します。したがって、nᵢ は複数の隣接ノードに位置する最終リソースを取得し、nᵢ がこれらのノードと潜在的な相互作用を持つ可能性があることを示唆します。

# 参考文献

1. Wu, et al (2016). SDTNBI: an integrated network and chemoinformatics tool for systematic prediction of drug–target interactions and drug repositioning. Briefings in Bioinformatics, bbw012. https://doi.org/10.1093/bib/bbw012
2. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
