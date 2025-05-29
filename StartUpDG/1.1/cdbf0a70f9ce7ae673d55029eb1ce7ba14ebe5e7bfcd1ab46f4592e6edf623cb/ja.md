```
make_periodic(md::MeshData{Dim}, is_periodic...) where {Dim}
make_periodic(md::MeshData{Dim}, is_periodic = ntuple(x -> true, Dim)) where {Dim}
make_periodic(md::MeshData, is_periodic = true)
```

新しい MeshData を返し、ノードマップ `mapP` と面マップ `FToF` が周期的になります。ここで、`is_periodic` は `Bool` のタプルで、`x`、`y`、または `z` 座標に周期的境界条件を課すかどうかを示します。
