```
pdimport(data, time, obs, sort;
    bl = 0,
    th = 0,
    limitrule::Union{Nothing, LimitRule} = nothing,
    warn = true)
```

表から薬力学データをインポートします：

  * `data` - データテーブル；
  * `time` - 観察時間；
  * `obs` - 観察値；
  * `sort` - ソートする列。

キーワード：

  * `bl` - ベースライン；
  * `th` - 閾値；
  * `limitrule` - 制限ルール；
  * `warn` - `false`の場合は警告を抑制。
