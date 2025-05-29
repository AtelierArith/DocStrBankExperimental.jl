```
NanosecondDateTime(str)
```

文字列から `NanosecondDateTime` を作成します。標準フォーマット `"yyyy-mm-ddTHH:MM:SS.s"` である必要があります。 （フィールドの説明については [`Dates.DateFormat`](@ref) を参照してください。）ナノ秒の精度を指定することはできますが、必須ではありません。

# 例

```
julia> NanosecondDateTime("1990-01-02T03:04:05.123456789")
NanosecondDateTime("1990-01-02T03:04:05.123456789")

julia> NanosecondDateTime("2000-01-01")
NanosecondDateTime("2000-01-01T00:00:00.000000000")
```
