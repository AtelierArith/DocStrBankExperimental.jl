```
am(dt::DateTime)::Bool
```

時間が午前であるかどうかを確認します。

# 引数

`dt`: DateTimeオブジェクト

# 戻り値

時間が午前であるかどうかを示すブール値。

# 例

```jldoctest
julia> am(DateTime(2023, 6, 15, 9, 30, 0))
true

julia> am(DateTime(2023, 6, 15, 8, 30, 0))
true
```
