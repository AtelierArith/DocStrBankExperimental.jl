```
fit(events::Array{<:Number, 1}, maxT::Number, its::Int64)
```

# 引数

  * `events` ハークス過程にフィットさせるイベント時間の配列。
  * `maxT` イベントが観測された境界時間。
  * `its` サンプリングする反復回数。

# 注意事項

  * すべての `events` はユニークでなければなりません。
