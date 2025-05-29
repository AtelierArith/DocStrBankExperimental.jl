```
convert_to_si(value, unit_name::String)
```

`value`を`unit_symbol`で与えられた単位からSI表現に変換します。

# 例

```jldoctest
julia> convert_to_si(1.0, :hour) # 1時間を秒として表現
3600.0
```
