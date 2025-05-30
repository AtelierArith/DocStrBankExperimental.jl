```
beta_carvalho(community_matrix::Community_Matrix)
```

コミュニティマトリックスにおける2つのコミュニティ間のベータ多様性をカルヴァーリョフレームワークに従って計算します。

# 引数

  * `community_matrix::Community_Matrix`: 2つのコミュニティの種データを含むコミュニティマトリックス。3つ以上のコミュニティが存在する場合、最初の2つのみが考慮されます。

# 戻り値

  * ベータ多様性の3つの成分：総不均一性、置換不均一性、及び豊富さ不均一性を含む配列。

# 詳細

この関数は、カルヴァーリョフレームワークを使用して2つのコミュニティ間のベータ多様性を計算します。このフレームワークは、ベータ多様性を3つの成分に分解します：総不均一性、置換不均一性、及び豊富さ不均一性。総不均一性は、2つのコミュニティ間の種構成の全体的な違いを測定します。置換不均一性は、1つのコミュニティの種が他のコミュニティの異なる種に置き換えられる程度を測定します。豊富さ不均一性は、2つのコミュニティ間の種の豊富さの違いを測定します。

# 参考文献

Carvalho, J. C., Cardoso, P., Borges, P. A. V., Schmera, D., & Podani, J. (2013). Measuring fractions of beta diversity and their relationships to nestedness: A theoretical and empirical comparison of novel approaches. Oikos, 122(6), 825-834. https://doi.org/10.1111/j.1600-0706.2012.20980.x
