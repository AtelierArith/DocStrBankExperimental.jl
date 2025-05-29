```
apply_adaboost_stumps_proba(stumps::Ensemble, coeffs, features, labels::AbstractVector)
```

各行の `features` に対して $P(L=label|X)$ を計算し、各行が1に合計される確率の `N_row` x `n_labels` 行列を返します。

`col_labels` は異なるラベルを含むベクトルで、例えば `["versicolor", "virginica", "setosa"]` です。その順序は出力行列の列の順序を決定します。

[`build_adaboost_stumps`](@ref) も参照してください。  ```
