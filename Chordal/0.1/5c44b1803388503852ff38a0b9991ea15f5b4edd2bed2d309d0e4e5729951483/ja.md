```
get_selectors(input_mat::SparseMatrixCSC; verbose=true, ret_cliques=true)
```

入力行列 `input_mat` のスパースパターンに対応するグラフの（マージされた）クリークを返します（フィルインを減らすための置換後）。オプションでクリークも返します。また、使用されたフィル削減置換とその逆置換も返します。
