```
CFTime.DateTime360Day(dt::AbstractString, format::AbstractString; locale="english") -> CFTime.DateTime360Day
```

`format` 文字列で指定されたパターンに従って `dt` 日付時刻文字列を解析することによって CFTime.DateTime360Day を構築します。

!!! note
    この関数は実験的であり、将来的に削除される可能性があります。`format` を解析するために `Dates` の内部関数に依存しています。

