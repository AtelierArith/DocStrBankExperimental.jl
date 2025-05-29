```
dmy_hm(datetime_string::Union{AbstractString, Missing})::DateTime
```

"DD-MM-YYYY HH:MM" 形式の日付と時刻の文字列を DateTime オブジェクトに変換します。

# 引数

`datetime_string`: 日時表現を含む文字列（DataFrame で欠損値を含む可能性があります）。

# 戻り値

入力文字列から解析された日、月、年、時、分の値から構築された DateTime オブジェクト。すべてが正常に解析できた場合に返されます。入力が欠損している場合や、文字列から日時情報を解析できない場合は、欠損値を返します。

# 例

```jldoctest
julia> dmy_hm("01/01/2020 4:30PM")
2020-01-01T16:30:00

julia> dmy_hm("01/01/2020 4:30 a")
2020-01-01T04:30:00

julia> dmy_hm(missing)
missing
```
