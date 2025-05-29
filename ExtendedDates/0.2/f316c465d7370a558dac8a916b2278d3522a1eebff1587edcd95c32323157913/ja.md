```
year(::UTInstant{<:Period})
```

年内の期間のサブ期間。番号は1から始まります。

```jldoctest
julia> subperiod(period(Day, 1960, 12))
12

julia> Date(period(Day, 1960, 12))
1960-01-12
```
