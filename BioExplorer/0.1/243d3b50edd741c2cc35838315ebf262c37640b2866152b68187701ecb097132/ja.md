```
beta_carvalho_matrix(community_matrix::Community_Matrix)
```

コミュニティマトリックスにおけるすべてのコミュニティペア間のベータ多様性マトリックスをカルヴァーリョフレームワークに従って計算します: Carvalho, J. C., Cardoso, P., Borges, P. A. V., Schmera, D., & Podani, J. (2013). Measuring fractions of beta diversity and their relationships to nestedness: A theoretical and empirical comparison of novel approaches. Oikos, 122(6), 825-834. https://doi.org/10.1111/j.1600-0706.2012.20980.x

# 引数

  * `community_matrix::Community_Matrix`: 複数のコミュニティの種データを含むコミュニティマトリックス。

# 戻り値

  * 総不似合い、置換不似合い、豊富さ不似合いのベータ多様性マトリックスを表す3つのDataFrameを含む配列。

# 詳細

この関数は、カルヴァーリョフレームワークを使用してすべてのコミュニティペア間のベータ多様性を計算します。このフレームワークは、ベータ多様性を3つの成分に分解します: 総不似合い、置換不似合い、豊富さ不似合い。各成分について、別々のDataFrameが返され、各行と列はコミュニティを表し、値は対応するコミュニティペア間のベータ多様性を表します。

[`beta_carvalho`](@ref)も参照してください。
