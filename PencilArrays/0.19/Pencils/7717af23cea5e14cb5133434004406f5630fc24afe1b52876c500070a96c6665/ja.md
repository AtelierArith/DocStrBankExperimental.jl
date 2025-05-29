```
localgrid(p::Pencil, (x_global, y_global, ...))      -> LocalRectilinearGrid
localgrid(u::PencilArray, (x_global, y_global, ...)) -> LocalRectilinearGrid
```

デコンポジション構成と一連の直交グローバル座標 `(x_global, y_global, ...)` から [`LocalRectilinearGrid`](@ref LocalGrids.LocalRectilinearGrid) を作成します。

この場合、各 `*_global` はグローバルグリッドの1次元に沿った座標を記述する `AbstractVector` です。
