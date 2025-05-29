```
plan_route!(agent, dest, pathfinder::AStar{D})
```

エージェントを現在の位置から `dest`（例えば `(1, 5)` または `(1.3, 5.2)` の位置）に移動させるための最短経路を計算し、提供された `pathfinder` を使用して保存します。

このメソッドは [`move_along_route!`](@ref) と組み合わせて使用します。
