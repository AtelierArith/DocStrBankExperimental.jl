```
Interpolate(domain; [options])
```

指定された `domain`（またはジオメトリのベクトル）を使用して、`options` のセットで geotable を補間します。

## オプション

  * `model` - GeoStatsModels.jl からのモデル（デフォルトは `NN()`）
  * `point` - 点サポートで補間を実行する（デフォルトは `true`）
  * `prob`  - 確率的補間を実行する（デフォルトは `false`）

## 例

```julia
# 最近傍モデル
Interpolate(grid, model=NN())

# 逆距離加重モデル
Interpolate(pset, model=IDW())
```

### 注意事項

補間はすべてのサンプル（すなわち geotable の行）を一度に実行されるため、Kriging のような一部のモデルには負担がかかる可能性があります。その場合は、[`InterpolateNeighbors`](@ref) を使用することをお勧めします。

他にも [`InterpolateNeighbors`](@ref) を参照してください。
