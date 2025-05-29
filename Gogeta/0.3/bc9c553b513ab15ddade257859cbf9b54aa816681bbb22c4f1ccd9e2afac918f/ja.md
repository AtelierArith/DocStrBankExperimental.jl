```
function get_solution(model::JuMP.Model, TE::TEModel)
```

最適化されたモデルに基づいて、各入力変数の上限と下限を見つけます。

各特徴の境界を配列で返します。

# 引数

  * `model`: 最適化されたJuMPモデル。
  * `TE`: ツリーアンサンブルに関する情報を含む`TEModel`型の構造体。
