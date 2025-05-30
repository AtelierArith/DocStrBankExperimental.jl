```
dayname(dt::TimeType; locale="english") -> String
dayname(day::Integer; locale="english") -> String
```

指定された`locale`の曜日に対応するフル曜日名を`Date`または`DateTime`の曜日に返します。また、`Integer`も受け付けます。

# 例

```jldoctest
julia> dayname(Date("2000-01-01"))
"Saturday"

julia> dayname(4)
"Thursday"
```
