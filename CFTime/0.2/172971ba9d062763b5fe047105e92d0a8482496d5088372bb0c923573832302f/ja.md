```
CFTime.DateTimeProlepticGregorian([Ti::DataType], y, [m, d, h, mi, s, ms, ...], origin = (1900, 1, 1), units = ...) -> CFTime.DateTimeProlepticGregorian
```

`CFTime.DateTimeProlepticGregorian` 型を年 (`y`)、月 (`m`, デフォルト 1)、日 (`d`, デフォルト 1)、時間 (`h`, デフォルト 0)、分 (`mi`, デフォルト 0)、秒 (`s`, デフォルト 0)、ミリ秒 (`ms`, デフォルト 0)、.... を用いて構築します。現在、`attosecond` がサポートされている最小の時間単位です。

すべての引数は `Int64` に変換可能でなければなりません。`CFTime.DateTimeProlepticGregorian` は `AbstractCFDateTime` のサブタイプです。

日付は、`origin`（エポック）からの経過時間を `milliseconds` として保存されますが、必要に応じて小さい時間単位が使用されます。たとえば、ユーザーが 8 つの整数を提供した場合、それらは年、月、日、時間、分、秒、ミリ秒、マイクロ秒として解釈されます。この場合、内部の時間単位はマイクロ秒になります。

netCDF CF カレンダーは [CF Standard](http://cfconventions.org/cf-conventions/cf-conventions.html#calendar) で定義されています。この型は「prolepticgregorian」として定義されたカレンダーを実装しています。
