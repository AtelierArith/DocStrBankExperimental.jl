```
StdCoords()
```

すべての幾何学の座標を区間 `[-0.5, 0.5]` に標準化します。

## 例

```julia
julia> CartesianGrid(10, 10) |> StdCoords()
10×10 CartesianGrid{2,Float64}
  minimum: Point(-0.5, -0.5)
  maximum: Point(0.5, 0.5)
  spacing: (0.1, 0.1)
```
