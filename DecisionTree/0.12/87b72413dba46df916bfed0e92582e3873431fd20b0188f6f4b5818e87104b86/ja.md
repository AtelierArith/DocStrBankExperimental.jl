```
apply_tree_proba(tree, features, col_labels::AbstractVector)
```

指定された `tree` に対して、各行の `features` に対して $P(L=label|X)$ を計算し、確率の `N_row` x `n_labels` 行列を返します。各行は合計が1になります。ここで `tree` は、例えば [`build_tree`](@ref) によって返される任意の `DecisionTree.Root`、`DecisionTree.Node` または `DecisionTree.Leaf` インスタンスです。

`col_labels` は、異なるラベルを含むベクトルで、例えば `["versicolor", "virginica", "setosa"]` です。その順序は出力行列の列の順序を決定します。

詳細は [`build_tree`](@ref) を参照してください。
