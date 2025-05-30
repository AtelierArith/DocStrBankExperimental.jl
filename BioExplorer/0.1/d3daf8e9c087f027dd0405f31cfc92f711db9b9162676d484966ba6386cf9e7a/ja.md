```
fit_gambin_plot(community_matrix::Community_Matrix, community_selected::String)
```

種の豊富さ分布と適合したガンマ二項（GamBin）モデルをプロットします。

# 引数

  * `community_matrix::Community_Matrix`: 種の豊富さデータを含むコミュニティマトリックス。
  * `community_selected::String`: モデルが適合され、プロットされるコミュニティの名前。

# 戻り値

  * 種の豊富さ分布と適合したGamBinモデルのプロットを表すMakie Figure。

# 詳細

この関数は、選択されたコミュニティの種の豊富さ分布をプロットし、適合したガンマ二項（GamBin）モデルを表示します。最初に`fit_gambin`関数を使用してGamBinモデルを適合させ、最適化されたパラメータ（α）を取得し、観測された豊富さ分布を棒グラフとしてプロットし、適合したモデルを同じ軸上に線グラフとしてプロットします。結果として得られるMakie Figureは、種の豊富さ分布と適合したGamBinモデルのプロットを表します。

他にも[`octave`](@ref)、[`octave_plot`](@ref)、[`fit_gambin`](@ref)を参照してください。

# 参考文献

Ugland, K. I., Lambshead, P. J. D., McGill, B., Gray, J. S., O’Dea, N., Ladle, R. J., & Whittaker, R. J. (2007). Modelling dimensionality in species abundance distributions: Description and evaluation of the Gambin model. Evolutionary Ecology Research, 9(2), 313–324.

Matthews, T. J., Borregaard, M. K., Ugland, K. I., Borges, P. A. V., Rigal, F., Cardoso, P., & Whittaker, R. J. (2014). The gambin model provides a superior fit to species abundance distributions with a single free parameter: Evidence, implementation and interpretation. Ecography, 37(10), 1002–1011. https://doi.org/10.1111/ecog.00861
