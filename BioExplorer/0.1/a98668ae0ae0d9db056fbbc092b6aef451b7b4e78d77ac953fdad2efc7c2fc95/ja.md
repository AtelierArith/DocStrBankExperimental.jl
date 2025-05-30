biodiversity*estimate(community*matrix::Community_Matrix)

コミュニティ内の種の数のいくつかの推定値を計算します。

# 引数

  * `community_matrix::Community_Matrix`: 入力コミュニティマトリックス。

# 戻り値

  * 推定値とそれに対応する値を含むDataFrame。

# 詳細

この関数は、発生または豊富さデータに基づいてコミュニティ内の種の数のいくつかの推定値を計算します。Jackknife1、Jackknife2、Chao1、およびChao2の種の豊富さの推定値を計算します。

[`sampling_coverage`](@ref) も参照してください。

# 参考文献

Chao, A., Chiu, C.-H., & Jost, L. (2014). Unifying Species Diversity, Phylogenetic Diversity, Functional Diversity, and Related Similarity and Differentiation Measures Through Hill Numbers. Annual Review of Ecology, Evolution, and Systematics, 45(1), 297–324. https://doi.org/10.1146/annurev-ecolsys-120213-091540
