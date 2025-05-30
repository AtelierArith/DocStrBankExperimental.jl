```
fit_gambin(community_matrix::Community_Matrix, community_selected::String)
```

種の豊富さ分布にGamma二項（GamBin）モデルを適合させます。

# 引数

  * `community_matrix::Community_Matrix`: 種の豊富さデータを含むコミュニティマトリックス。
  * `community_selected::String`: モデルを適合させるコミュニティの名前。

# 戻り値

  * Gamma二項モデルの最適化されたパラメータ（α）。

# 詳細

この関数は、選択されたコミュニティの種の豊富さ分布にGamma二項（GamBin）モデルを適合させます。モデルは、GamBinモデルの下で与えられた豊富さ分布を観察する可能性を最大化するパラメータ（α）の最適値を見つけるために、最尤推定を使用して適合されます。

他にも[`octave`](@ref)、[`octave_plot`](@ref)、[`fit_gambin_plot`](@ref)を参照してください。

# 参考文献

Ugland, K. I., Lambshead, P. J. D., McGill, B., Gray, J. S., O’Dea, N., Ladle, R. J., & Whittaker, R. J. (2007). 種の豊富さ分布における次元性のモデリング：Gambinモデルの説明と評価。進化生態学研究, 9(2), 313–324。

Matthews, T. J., Borregaard, M. K., Ugland, K. I., Borges, P. A. V., Rigal, F., Cardoso, P., & Whittaker, R. J. (2014). Gambinモデルは単一の自由パラメータを持つ種の豊富さ分布に優れた適合を提供します：証拠、実装、および解釈。生態地理学, 37(10), 1002–1011。 https://doi.org/10.1111/ecog.00861
