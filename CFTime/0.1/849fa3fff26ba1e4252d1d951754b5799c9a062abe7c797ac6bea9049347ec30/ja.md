```
CFTime.DateTimeAllLeap(y, [m, d, h, mi, s, ms]) -> CFTime.DateTimeAllLeap
```

年（`y`）、月（`m`、デフォルト1）、日（`d`、デフォルト1）、時間（`h`、デフォルト0）、分（`mi`、デフォルト0）、秒（`s`、デフォルト0）、ミリ秒（`ms`、デフォルト0）によって `CFTime.DateTimeAllLeap` 型を構築します。すべての引数は `Int64` に変換可能でなければなりません。`CFTime.DateTimeAllLeap` は `AbstractCFDateTime` のサブタイプです。

netCDF CF カレンダーは [CF Standard](http://cfconventions.org/cf-conventions/cf-conventions.html#calendar) で定義されています。この型は「allleap」として定義されたカレンダーを実装しています。
