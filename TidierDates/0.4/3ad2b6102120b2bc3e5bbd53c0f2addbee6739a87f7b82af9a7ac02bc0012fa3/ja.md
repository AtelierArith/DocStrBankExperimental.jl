```
mdy_hms(datetime_string::Union{AbstractString, Missing})
```

月、日、年、時、分、秒の値を含むことが期待される日時文字列を解析します。

# 引数

`datetime_string`: 日時表現を含む文字列（DataFrame内で欠損値を含むことができます）。

# 戻り値

入力文字列から解析された月、日、年、時、分、秒の値から構築されたDateTimeオブジェクト。すべてが正常に解析できた場合に返されます。入力が欠損している場合や、文字列から日時情報を解析できない場合は、欠損値を返します。

# 例

```jldoctest
julia> mdy_hms("06/15/2023 08:30:15")
2023-06-15T08:30:15

julia> mdy_hms("06.15.2023.08.30.15")
2023-06-15T08:30:15

julia> mdy_hms("06.15.2023.08.30.15 pm")
2023-06-15T20:30:15

julia> mdy_hms("06152023083015")
2023-06-15T08:30:15

julia> mdy_hms(missing)
missing
```
