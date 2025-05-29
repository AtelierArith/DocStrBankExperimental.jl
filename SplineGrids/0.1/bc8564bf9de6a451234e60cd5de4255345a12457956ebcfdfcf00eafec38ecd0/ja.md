```
LocalRefinement(
    dims_refinement,
    refinement_matrices,
    refinement_indices,
    refinement_values)
```

ローカルリファインメントを実行するためのデータ。1つ以上のリファインメント行列と、指定された次元に沿ってリファインメント行列との乗算後に上書きされる制御点の値。

## フィールド

  * `dims_refinement`: リファインメントが行われる次元
  * `refinement_matrices`: リファインメントを実行する行列
  * `refinement_indices`: リファインメント後に上書きされる制御点のインデックス
  * `refinement_values`: リファインメント後に書き換えられる制御点の新しい値
