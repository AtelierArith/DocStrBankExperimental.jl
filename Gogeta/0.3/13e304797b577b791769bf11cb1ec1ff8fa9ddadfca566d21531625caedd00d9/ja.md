```
function tree_callback_algorithm(cb_data, TE::TEModel, opt_model::JuMP.Model)
```

遅延制約を使用したツリーアンサンブル最適化のためのコールバックアルゴリズムです。

遅延制約を使用して、分割制約は各ツリーごとに1つずつ追加されます。

遅延制約の使用方法については、例やドキュメントを参照してください。

# 引数

  * `cb_data`: コールバックデータ
  * `TE`: ユニバーサルデータ型 `TEModel` のツリーアンサンブルモデル。
  * `opt_model`: 定式化を含むJuMPモデル。
