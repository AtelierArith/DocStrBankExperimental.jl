```
pm(dt::DateTime)::Bool
```

午後であるかどうかをチェックします。

# 引数

`dt`: DateTimeオブジェクト

# 戻り値

時間が午後であるかどうかを示すブール値。

# 例

```jldoctest
julia> pm(DateTime(2023, 6, 15, 9, 30, 0))
false

julia> pm(DateTime(2023, 6, 15, 8, 30, 0))
false
```
