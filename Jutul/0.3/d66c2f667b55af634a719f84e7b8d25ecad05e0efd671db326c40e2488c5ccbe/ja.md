```
convert_from_si(value, unit_name::Union{Symbol, String})
```

`value`をSI表現から`unit_symbol`の単位に変換します。

# 例

```jldoctest
julia> convert_from_si(3600.0, :hour) # 3600秒を時間として表現
1.0
```
