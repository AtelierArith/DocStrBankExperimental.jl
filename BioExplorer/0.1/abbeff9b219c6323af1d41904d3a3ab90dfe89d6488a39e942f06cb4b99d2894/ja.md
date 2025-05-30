```
jaccard_dissim_matrix(community_matrix::Community_Matrix)
```

コミュニティマトリックス内のすべてのコミュニティ間のジャッカード非類似性行列を計算します。

# 引数

  * `community_matrix::Community_Matrix`: 複数のコミュニティの種データを含むコミュニティマトリックス。

# 戻り値

  * `beta_matrix::DataFrame`: すべてのコミュニティペア間のジャッカード非類似性行列を表すDataFrame。

# 詳細

この関数は、指定されたコミュニティマトリックス内のすべてのコミュニティペア間のジャッカード非類似性を計算します。すべての可能なコミュニティの組み合わせを反復処理し、`jaccard_dissim`関数を使用してジャッカード非類似性を計算します。結果はDataFrameに格納され、各行と列はコミュニティを表し、値は対応するコミュニティペア間のジャッカード非類似性を表します。

他にも [`jaccard_dissim`](@ref) を参照してください。
