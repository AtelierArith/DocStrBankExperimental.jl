```julia
GetIndexPath(start::Vector{Int64}, ending::Vector{Int64} ; exclusive::Bool=true) --> Vector{Vector{Int64}}
```

2つのインデックスセット `start` と `ending` を結ぶ離散格子のインデックス空間におけるパスを返します。入力の `exclusive` が `true` に設定されている場合、返されるパスには `ending` ポイント自体は含まれません。任意の次元で動作します。
