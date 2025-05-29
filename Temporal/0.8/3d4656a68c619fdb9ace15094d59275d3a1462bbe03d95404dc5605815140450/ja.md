```
ojoin(x::TS,y::TS)::TS
```

インデックスによって2つのTSオブジェクトを外部結合します。

`x` OUTER JOIN `y` ON `x.index` = `y.index` に相当します。

...

# 引数

  * `x::TS`: 結合の左側。
  * `y::TS`: 結合の右側。

...
