```
@assert_matrix(matrix::Any, [n_rows::Integer, n_columns::Integer], [major_axis::Int8])
```

`matrix`が`AbstractMatrix`であり、オプションで`n_rows`と`n_columns`を持つことを確認します。`major_axis`が指定されている場合、`check_efficient_action`を呼び出して、行列が効率的なレイアウトであることを確認します。
