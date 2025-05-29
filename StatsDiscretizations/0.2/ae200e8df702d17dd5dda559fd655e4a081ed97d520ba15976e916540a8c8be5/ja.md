```
RealLineDiscretizer{L, R, T, G <:AbstractVector{T}} <: AbstractRealLineDiscretizer{Interval{L, R, T}}
```

与えられたポイントのグリッドに基づいて実数直線を区間に分割する拡張連続離散化器です。グリッドを超えて、-∞から最初のグリッドポイントまで、最後のグリッドポイントから+∞までの区間を含めることで離散化を拡張します。

型パラメータ `L` と `R` は区間の端点の型（例：`Closed` または `Open`）を指定し、`T` はグリッドの要素型、`G` はグリッドベクターの型です。

# フィールド

  * `grid::G`: 離散化に使用されるポイントのグリッド。

# 例

```julia
grid = [0.0, 1.0, 2.0]
discr = RealLineDiscretizer{Closed,Open}(grid)
```
