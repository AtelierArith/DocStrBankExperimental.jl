```
compute_extreme_point(lmo::ProductLMO, direction::AbstractArray; direction_indices, storage=similar(direction))
```

極値点の計算。方向配列と `direction_indices` が提供され、`direction[direction_indices[i]]` が i 番目の LMO に渡されます。`direction_indices` が提供されていない場合、方向配列は最後の次元に沿ってスライスされ、`direction[:, ... ,:, i]` が i 番目の LMO に渡されます。結果はオプションの `storage` コンテナに格納されます。

すべてのキーワード引数はすべての LMO に渡されます。
