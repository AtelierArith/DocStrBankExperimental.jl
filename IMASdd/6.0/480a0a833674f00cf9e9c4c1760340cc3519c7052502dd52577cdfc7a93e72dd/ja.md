```
get_time_array(@nospecialize(ids::IDS), field::Symbol, time0::Float64, scheme::Symbol=:constant)
```

時間依存配列からデータを取得します

注意: @ddtime 配列処理のロジック:

  * 補間 (i) `scheme` 配列の境界間
  * 定数 (c) 時間配列の境界内での外挿
  * エラー (e) time0 が最小(time) より前の場合

例えば:

```
time:   -oooo-
data:   -o-o--
ddtime: eiiicc
```
