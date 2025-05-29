```
year(::UTInstant{<:Period})
```

期間の年。

```jldoctest
julia> year(period(Day, 1960, 12))
1960
```
