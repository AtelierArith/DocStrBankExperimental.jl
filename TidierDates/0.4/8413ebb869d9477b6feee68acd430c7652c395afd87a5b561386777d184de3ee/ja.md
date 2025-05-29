```
ymd_h(datetime_string::Union{AbstractString, Missing})::DateTime
```

"YYYY-MM-DD HH" 形式の日時文字列を DateTime オブジェクトに変換します。

# 引数

`datetime_string`: 日時表現を含む文字列（DataFrame で欠損値を含むことができます）。

# 戻り値

入力文字列から解析された年、月、日、時の値から構築された DateTime オブジェクト。すべてが正常に解析できた場合に返されます。入力が欠損している場合や、文字列から日時情報を解析できない場合は、欠損値を返します。

# 例

```jldoctest
julia> ymd_h("2023-06-15 09hr")
2023-06-15T09:00:00

julia> ymd_h("2023-06-15 09hr p")
2023-06-15T21:00:00

julia> ymd_h(missing)
missing
```
