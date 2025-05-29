```
write_stationfile(stationfile::AbstractString, stdat::Station)
write_stationfile(stationfile::AbstractString, stdat::AbstractVector{Station})
```

Ticra POS4互換の最適化ステーションファイルを書きます。ここで、`stdat`がベクトルの場合、その要素はステーションファイル内のパーティションです。
