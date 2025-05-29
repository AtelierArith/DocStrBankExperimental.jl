```
Rasterize(grid)
Rasterize(grid, var₁ => agg₁, ..., varₙ => aggₙ)
```

指定された `grid` 内のジオメトリをラスタライズします。

```
Rasterize(nx, ny)
Rasterize(nx, ny, var₁ => agg₁, ..., varₙ => aggₙ)
```

また、バウンディングボックスの離散化によって得られたサイズ `nx` x `ny` のグリッドを使用します。

変数 `varᵢ` の重複は、集約関数 `aggᵢ` で集約されます。変数 `varᵢ` に対して集約関数が定義されていない場合、デフォルトの集約関数が使用されます。デフォルトの集約関数は、連続変数の場合は `mean`、それ以外の場合は `first` です。

# 例

```julia
grid = CartesianGrid(10, 10)
Rasterize(grid)
Rasterize(10, 10)
Rasterize(grid, 1 => last, 2 => maximum)
Rasterize(10, 10, 1 => last, 2 => maximum)
Rasterize(grid, :a => first, :b => minimum)
Rasterize(10, 10, :a => first, :b => minimum)
Rasterize(grid, "a" => last, "b" => maximum)
Rasterize(10, 10, "a" => last, "b" => maximum)
```
