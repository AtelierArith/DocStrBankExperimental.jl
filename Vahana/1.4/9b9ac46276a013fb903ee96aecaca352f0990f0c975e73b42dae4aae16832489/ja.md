```
move_to!(sim, name::Symbol, id::AgentID, pos, edge_from_raster, edge_to_raster; [distance = 0, metric = :chebyshev, periodic = true])
```

エージェントID `id` を持つエージェントと、位置 `pos` にあるラスタ `name` のセルとの間に、最大2つのタイプのエッジを作成します。

`pos` は CartesianIndex または Dims{N} の型でなければなりません。

`edge_from_raster` は、セルをソースノード、エージェントをターゲットノードとして追加されるエッジです。`edge_from_raster` は `nothing` であることができ、この場合、エージェントをターゲットノードとしてエッジは追加されません。

`edge_to_raster` は、エージェントをソースノード、セルをターゲットノードとして追加されるエッジです。`edge_to_raster` は `nothing` であることができ、この場合、エージェントをソースノードとしてエッジは追加されません。

キーワード引数を使用すると、位置 `pos` にあるセルの周囲に追加のエッジを同じラスタ内で追加することが可能です。つまり、メトリック `metric` の下で距離 `distance` にあるすべてのセルに対して、妥当なメトリックは `:chebyshev`、`:euclidean`、および `:manhatten` です。そして、キーワード `periodic` は、すべての次元が周期的であるかどうかを決定します。

`only_surrounding` キーワードが true に設定されている場合、`pos` の周囲のセルへのエッジのみが作成され、位置 `pos` 自体のセルへのエッジは作成されません。

[`add_raster!`](@ref) および [`connect_raster_neighbors!`](@ref) も参照してください。
