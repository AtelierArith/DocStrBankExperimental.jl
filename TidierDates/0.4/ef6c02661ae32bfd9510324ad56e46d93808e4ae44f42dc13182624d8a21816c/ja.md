```
ymd_hm(datetime_string::Union{AbstractString, Missing})::DateTime
```

"YYYY-MM-DD HH:MM" 形式の日時文字列を DateTime オブジェクトに変換します。

# 引数

`datetime_string`: 日時表現を含む文字列（DataFrame で欠損値を含む可能性があります）。

# 戻り値

入力文字列から解析された年、月、日、時、分の値から構築された DateTime オブジェクト。すべてが正常に解析できた場合に返されます。入力が欠損している場合や、文字列から日時情報を解析できない場合は、欠損値を返します。

# 例

```jldoctest
julia> ymd_hm("2023-06-15 09:30")
2023-06-15T09:30:00

julia> ymd_hm("2023-06-15 09:30p")
2023-06-15T21:30:00

julia> ymd_hm(missing)
missing
```
