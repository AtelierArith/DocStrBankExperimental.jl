```
ijoin(x::TS,y::TS)::TS
```

インデックスによって2つのTSオブジェクトを内部結合します。

`x` INNER JOIN `y` が `x.index` = `y.index` に相当します。

...

# 引数

  * `x::TS`: 結合の左側。
  * `y::TS`: 結合の右側。

...
