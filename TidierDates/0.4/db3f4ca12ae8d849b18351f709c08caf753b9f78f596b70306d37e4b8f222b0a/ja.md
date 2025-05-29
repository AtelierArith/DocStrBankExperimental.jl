```
mdy_h(datetime_string::Union{AbstractString, Missing})::DateTime
```

"MM-DD-YYYY HH" 形式の日付と時刻の文字列を DateTime オブジェクトに変換します。

# 引数

`datetime_string`: 日時表現を含む文字列（DataFrame で欠損値を含む可能性があります）。

# 戻り値

入力文字列から解析された月、日、年、時の値から構築された DateTime オブジェクト。すべてが正常に解析できた場合に返されます。入力が欠損している場合や、文字列から日時情報を解析できない場合は、欠損値を返します。

# 例

```jldoctest
julia> mdy_h("06-15-2023 09hr")
2023-06-15T09:00:00

julia> mdy_h("06-15-2023 09hr pM")
2023-06-15T21:00:00

julia> mdy_h("jan 3 2023 09hr p")
2023-01-03T21:00:00

julia> mdy_h(missing)
missing
```
