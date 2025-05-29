```
ymd(date_string::Union{AbstractString, Missing})
```

さまざまな形式の日時文字列（「yyyymmdd」、「yyyy/mm/dd」、「yyyy-mm-dd」、または「年 月 日」など）をJuliaのDateオブジェクトに変換します。この関数は欠損値を処理でき、欠損入力に対しては欠損を返します。

# 引数

date_string::Union{AbstractString, Missing}: Dateオブジェクトに変換される日時文字列。

# 例

```jldoctest
julia> ymd("20201203")
2020-12-03

julia> ymd("2020/12/03")
2020-12-03

julia> ymd("2020-12-03")
2020-12-03

julia> ymd("2020 12 03")
2020-12-03

julia> ymd("2020 December 3rd")
2020-12-03

julia> ymd(missing)
missing
```
