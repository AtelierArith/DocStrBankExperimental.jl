```
days_in_month(date::Date)::Int
```

月の日数を返します。

# 引数

`date`: Dateオブジェクト

# 返り値

月の日数を表す整数。

# 例

```jldoctest
julia> days_in_month(Date(2023, 6, 15))
30

julia> days_in_month(Date(2020, 2, 29))
29

julia> days_in_month(Date(2019, 2, 28))
28

julia> days_in_month(Date(2016, 2, 3))
29
```
