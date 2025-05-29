```
function TE_formulate!(opt_model::JuMP.Model, TE::TEModel, objective)
```

与えられたツリーアンサンブル `TE` に基づいて、JuMP モデル `opt_model` にツリーアンサンブルを定式化します。

JuMP モデルは、スプリット制約なしで定式化されます。

アンサンブル出力を最小化または最大化する目的関数が `JuMP` モデルに追加されます。

# 引数

  * `opt_model`: 定式化が保存される `JuMP` モデル。
  * `TE`: ユニバーサルデータ型 `TEModel` のツリーアンサンブルモデル。
  * `objective`: MIN*SENSE または MAX*SENSE。ツリーアンサンブル出力を最小化または最大化します。
