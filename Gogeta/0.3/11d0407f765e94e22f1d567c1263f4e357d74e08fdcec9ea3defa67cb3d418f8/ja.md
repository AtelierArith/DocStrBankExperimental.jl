```
function add_split_constraints!(opt_model::JuMP.Model, TE::TEModel)
```

すべての分割制約を定式化に追加します。

# 引数

  * `opt_model`: 定式化を含むJuMPモデル。
  * `TE`: ユニバーサルデータ型`TEModel`のツリーアンサンブルモデル。
