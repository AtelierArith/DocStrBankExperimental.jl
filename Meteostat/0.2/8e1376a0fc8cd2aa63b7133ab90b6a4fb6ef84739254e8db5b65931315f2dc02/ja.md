```
function filter_inventory!(
    stations, granularity::Type{T}, period::Tuple{Dates.Date,Dates.Date}
)
```

2つの日付の間の在庫データによって気象観測所をフィルタリングします（通常値には`nothing`を渡します）
