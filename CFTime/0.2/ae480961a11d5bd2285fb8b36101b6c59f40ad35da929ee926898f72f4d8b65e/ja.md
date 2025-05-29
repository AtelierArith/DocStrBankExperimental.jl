```
CFTime.DateTimeJulian([Ti::DataType], y, [m, d, h, mi, s, ms, ...], origin = (1900, 1, 1), units = ...) -> CFTime.DateTimeJulian
```

年（`y`）、月（`m`、デフォルトは1）、日（`d`、デフォルトは1）、時間（`h`、デフォルトは0）、分（`mi`、デフォルトは0）、秒（`s`、デフォルトは0）、ミリ秒（`ms`、デフォルトは0）、.... を指定して `CFTime.DateTimeJulian` 型を構築します。現在、`attosecond` がサポートされている最小の時間単位です。

すべての引数は `Int64` に変換可能でなければなりません。`CFTime.DateTimeJulian` は `AbstractCFDateTime` のサブタイプです。

日付は、`origin`（エポック）からの経過時間をミリ秒で表現して保存されますが、必要に応じて小さい時間単位が使用されます。たとえば、ユーザーが8つの整数を提供した場合、それらは年、月、日、時間、分、秒、ミリ秒、マイクロ秒として解釈されます。この場合、内部の時間単位はマイクロ秒になります。

netCDF CF カレンダーは [CF標準](http://cfconventions.org/cf-conventions/cf-conventions.html#calendar) で定義されています。この型は「ユリウス」として定義されたカレンダーを実装しています。
