```
function filter_inventory!(
    stations, granularity::Type{T}, date::Dates.Date
)
```

特定の日の在庫データに基づいて気象観測所をフィルタリングします（通常値には `nothing` を渡します）
