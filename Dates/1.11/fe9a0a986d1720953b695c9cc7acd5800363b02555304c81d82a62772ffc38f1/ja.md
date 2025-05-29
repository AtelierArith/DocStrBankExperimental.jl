```
dayabbr(dt::TimeType; locale="japanese") -> String
dayabbr(day::Integer; locale="japanese") -> String
```

与えられた `locale` における `Date` または `DateTime` の曜日に対応する省略名を返します。`Integer` も受け付けます。

# 例

```jldoctest
julia> dayabbr(Date("2000-01-01"))
"土"

julia> dayabbr(3)
"水"
```
