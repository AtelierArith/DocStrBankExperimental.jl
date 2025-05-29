```
CFTime.DateTimeStandard(dt::AbstractString, format::AbstractString; locale="english") -> CFTime.DateTimeStandard
```

`format` 文字列で指定されたパターンに従って `dt` 日付時刻文字列を解析することによって CFTime.DateTimeStandard を構築します。

!!! note
    この関数は実験的であり、将来的に削除される可能性があります。`format` を解析するために `Dates` の内部関数に依存しています。

