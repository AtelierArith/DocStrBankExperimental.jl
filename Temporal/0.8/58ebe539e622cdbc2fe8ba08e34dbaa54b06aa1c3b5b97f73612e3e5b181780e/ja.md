```
ljoin(x::TS, y::TS)::TS
```

インデックスによって2つのTSオブジェクトを左結合します。

`x` LEFT JOIN `y` ON `x.index` = `y.index` と同等です。

...

# 引数

  * `x::TS`: 結合の左側。
  * `y::TS`: 結合の右側。

...
