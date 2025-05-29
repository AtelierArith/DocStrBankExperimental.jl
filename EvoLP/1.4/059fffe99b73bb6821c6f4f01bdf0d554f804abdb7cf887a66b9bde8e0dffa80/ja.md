```
compute!(logger::Logbook, data::AbstractVector)
compute!(notebooks::Vector{Logbook}, data::Vector{AbstractVector})
```

`logger`（または `logger` のベクトル）のために `data` を使用して統計を計算します。通常、`data` はフィットネスのベクトルです。すべての計算はインプレースで行われるため、`logger` の記録が更新されます。
