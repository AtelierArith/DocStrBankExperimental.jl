```
draw_counterfactual(scm::StructuralCausalModel, parents::CausalTable, intervention::Function) -> Vector
```

与えられた構造的因果モデル（SCM）、応答親のテーブル、および介入関数に基づいて反実的な応答を生成します。つまり、構造的因果モデルによって指定された治療に対して介入が適用されていた場合に発生したであろう応答をサンプリングします。

# 引数

  * `scm::StructuralCausalModel`: 反実的な結果を生成するために使用される構造的因果モデル。
  * `parents::CausalTable`: 応答変数の因果的に前にある変数を含むテーブル。
  * `intervention::Function`: 親変数に適用される介入を定義する関数。治療ベクトルまたは行列に作用する関数を `CausalTable` に作用する関数に変換するには `cast_matrix_to_table_function` を使用します。

# 戻り値

反実的な応答のベクトル。
