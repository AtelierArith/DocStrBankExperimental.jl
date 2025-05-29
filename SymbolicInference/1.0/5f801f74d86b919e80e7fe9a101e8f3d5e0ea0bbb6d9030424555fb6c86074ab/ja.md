```
rec_matrix_motifs(rec_matrix::RecurrenceMatrix;seqs="recurrences",window_range=collect(1:6),n_motifs=2)
```

オフ対角線における連続した実行に関連する確率のセットを返します。

引数 `seqs` は連続したシーケンスのタイプを設定します： 'double'（再発と非再発）、 'recurrences' または 'poincare'（非再発）のいずれかです。 `window_range` 引数によって与えられる対角線が考慮され、各対角線に対して n*motifs が考慮されます。 記号的構造の定義については `AnalyticComb.weighted*bin*runs*prob` を参照してください。  
