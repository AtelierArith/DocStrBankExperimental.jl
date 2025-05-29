```
leap_year(date::Date)::Bool
leap_year(date::Int)::Bool
```

年がうるう年かどうかをチェックします。

# 引数

`date`: 日付オブジェクトまたは年を表す整数。

# 戻り値

年がうるう年であるかどうかを示すブール値。

# 例

```jldoctest
julia> leap_year(Date(2023, 6, 15))
false

julia> leap_year(2020)
true
```
