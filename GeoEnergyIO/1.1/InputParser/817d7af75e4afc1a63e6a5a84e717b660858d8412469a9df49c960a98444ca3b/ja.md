```
number_of_tables(outer_data, t::Symbol)
```

指定されたタイプ`t`の宣言されたテーブルの数。次のいずれかである必要があります：

  * `:satnum`（飽和関数領域）
  * `:pvtnum`（PVT関数領域）
  * `:eqlnum`（平衡領域）
  * `:eosnum`（状態方程式領域）
