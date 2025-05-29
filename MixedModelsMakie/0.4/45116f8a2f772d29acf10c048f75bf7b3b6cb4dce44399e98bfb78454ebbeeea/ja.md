```
ranefinfotable(ri::RanefInfo)
```

`ri`の情報を列テーブル（`Vector`の`NamedTuple`）として返します。

列は次の通りです。

  * `name`: ランダム効果の名前
  * `level`: グループ化因子のレベル
  * `cmode`: ランダム効果の条件付きモード
  * `cstddev`: ランダム効果の条件付き標準偏差
