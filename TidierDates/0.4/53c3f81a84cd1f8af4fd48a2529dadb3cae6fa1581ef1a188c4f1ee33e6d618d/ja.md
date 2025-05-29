```
dmy(date_string::Union{AbstractString, Missing})
```

さまざまな形式の日時文字列（「ddmmyyyy」、「day month, year」、「d/m/y」、「d-m-y」または「day of month, year」など）をJuliaのDateオブジェクトに変換します。この関数は欠損値を処理でき、欠損の入力に対しては欠損を返します。

# 引数

`date_string`::Union{AbstractString, Missing}: Dateオブジェクトに変換される日時文字列。

# 例

```jldoctest
julia> dmy("03122020")
2020-12-03

julia> dmy("3 December, 2020")
2020-12-03

julia> dmy("23/12/2020")
2020-12-23

julia> dmy("3-12-2020")
2020-12-03

julia> dmy("3rd of December, 2020")
2020-12-03

julia> dmy("3rd of December, 2020")
2020-12-03

julia> dmy(missing)
missing
```
