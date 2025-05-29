```
filter_inventory!(stations, granularity::Type{T}) where {T<:Union{Dates.Period,Nothing}}
```

在庫データによって気象観測所をフィルタリングします（通常値には `nothing` を渡します）
