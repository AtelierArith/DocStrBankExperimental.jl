```
rjoin(x::TS, y::TS)::TS
```

インデックスによって2つのTSオブジェクトを右結合します。

`x` RIGHT JOIN `y` ON `x.index` = `y.index` と同等です。

...

# 引数

  * `x::TS`: 結合の左側。
  * `y::TS`: 結合の右側。

...
