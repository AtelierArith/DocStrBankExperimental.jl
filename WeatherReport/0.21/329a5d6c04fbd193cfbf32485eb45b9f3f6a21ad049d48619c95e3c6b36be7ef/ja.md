```
show_current(city::String, i_row::Int64 = 1)
```

指定された都市の現在の天候条件を表示します。

# 引数

  * `city::String` : 有効な都市名、例："Oslo"、"Paris"、"Amsterdam"など。
  * `i_row::Int64` : 指定された場所に対して複数の一致がある場合、                  印刷されたDataFrameから行インデックスを提供することで                  希望のタイムゾーンを選択します。デフォルトは1に設定されています。

# 例

```julia-repl
julia> show_current("Lisbon")
[ Info: 複数の一致が見つかりました。行1の場所のレポートを表示しています。
[ Info: 行インデックスによって別の場所を選択できます。
8×4 DataFrame
 Row │ CITY     TIMEZONE          LATITUDE  LONGITUDE 
     │ String?  String31          Float64   Float64   
─────┼────────────────────────────────────────────────
   1 │ Lisbon   Europe/Lisbon      38.7167   -9.13333
   2 │ Lisbon   America/New_York   39.8609  -83.6352
   3 │ Lisbon   America/New_York   41.604   -72.0117
   4 │ Lisbon   America/Chicago    41.9211  -91.3855
   5 │ Lisbon   America/New_York   44.0315  -70.1045
   6 │ Lisbon   America/Chicago    46.4416  -97.6812
   7 │ Lisbon   America/New_York   44.2134  -71.9109
   8 │ Lisbon   America/New_York   40.772   -80.7681
┌───────────────┬───────────┬────────────┬─────────────┬───────────┬─────────┬─────────┐
│      Timezone │ Elevation │ Wind speed │ Temperature │ Condition │      🌅 │      🌆 │
│         [WET] │       [m] │     [km/h] │        [°C] │        [] │ [hh:mm] │ [hh:mm] │
├───────────────┼───────────┼────────────┼─────────────┼───────────┼─────────┼─────────┤
│ Europe/Lisbon │      48.0 │        9.1 │        12.5 │ Clear sky │    7:18 │   18:21 │
└───────────────┴───────────┴────────────┴─────────────┴───────────┴─────────┴─────────┘
```
