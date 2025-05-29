```
mdy(date_string::Union{AbstractString, Missing})
```

さまざまな形式の日時文字列（「mmddyyyy」、「month day, year」、「m/d/y」、または「m-d-y」など）をJuliaのDateオブジェクトに変換します。この関数は欠損値を処理でき、欠損入力に対しては欠損を返します。

# 引数

`date_string`::Union{AbstractString, Missing}: Dateオブジェクトに変換される日時文字列。

# 例

```jldoctest
julia> mdy("12032020")
2020-12-03

julia> mdy("December 3, 2020")
2020-12-03

julia> mdy("12/03/2020")
2020-12-03

julia> mdy("12-03-2020")
2020-12-03

julia> mdy("1 24 2023")
2023-01-24

julia> mdy("01 24 2023")
2023-01-24

julia> mdy(missing)
missing

julia> mdy("FÉVRIER 20 2020") # フランス語
2020-02-20
```
