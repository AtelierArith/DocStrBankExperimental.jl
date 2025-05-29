```
InterpolateNeighbors(domain; [options])
```

指定された `domain`（またはジオメトリのベクトル）に対して、オプションのセットを使用して隣接検索でジオテーブルを補間します。

## オプション

  * `model`        - GeoStatsModels.jl からのモデル（デフォルトは `NN()`）
  * `path`         - ドメイン上のパス（デフォルトは `LinearPath()`）
  * `point`        - 点サポートで補間を実行する（デフォルトは `true`）
  * `prob`         - 確率的補間を実行する（デフォルトは `false`）
  * `minneighbors` - 最小隣接数（デフォルトは `1`）
  * `maxneighbors` - 最大隣接数（デフォルトは `10`）
  * `neighborhood` - 検索する近隣（デフォルトは `nothing`）
  * `distance`     - Distances.jl で定義された距離（デフォルトは `Euclidean()`）

2つの隣接検索方法が利用可能です：

  * `neighborhood` が提供されている場合、ドメイン内で `neighborhood` をスライドさせてローカル予測が行われます（例：`MetricBall`）。
  * `neighborhood` が提供されていない場合、`distance` に従って `maxneighbors` 最近傍を使用して予測が行われます。

## 例

```julia
# 10個の近くのサンプルを持つ多項式モデル
InterpolateNeighbors(grid, model=Polynomial(), maxneighbors=10)

# 100m半径内のサンプルを持つ逆距離加重モデル
InterpolateNeighbors(pset, model=IDW(), neighborhood=MetricBall(100u"m"))
```

### 注意事項

補間は近くのサンプルのサブセットで実行されます。これは、特にサンプル数が少ない場合に望ましくないアーティファクトを引き起こす可能性があります。その場合は、[`Interpolate`](@ref) を使用することをお勧めします。

他にも [`Interpolate`](@ref) を参照してください。
