```
ymd_hms(datetime_string::Union{AbstractString, Missing})
```

"年-月-日 時:分:秒" 形式の文字列を DateTime オブジェクトに変換します。

# 引数

`datetime_string`: 文字列（DataFrame に欠損値を含むことができます）。

# 戻り値

文字列から変換された DateTime オブジェクト。入力が欠損しているか、文字列形式が不正な場合、関数は欠損値を返します。

# 例

```jldoctest
julia> ymd_hms("2023-06-15 09:30:00")
2023-06-15T09:30:00

julia> ymd_hms("2023/06/15 09:30:00")
2023-06-15T09:30:00

julia> ymd_hms("2023/06/15 09:30:00pm")
2023-06-15T21:30:00

julia> ymd_hms("2023 June 15 09:30:00am")
2023-06-15T09:30:00 

julia> ymd_hms("2023 June 15 09:30:00 P")
2023-06-15T21:30:00

julia> ymd_hms(missing)
missing
```
