```
@mutate_node!(node, args...)
```

ノードをその場で変更します。

# 引数

  * `node`: 変更するノード
  * `args...`: ノードに適用する計算（例を参照）

# 参照

[`@mutate_mtg!`](@ref) を使用して、mtgのすべてのノードを変更します。

# 例

```julia
# パッケージからmtgをインポートする:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# スケールを使って新しい属性を計算し、その値に2を加えます:
@mutate_node!(mtg, scaling = node.scales .+ 2)

# 計算はルートノードにのみ適用されます。すべてのノードに適用するには、
# @mutate_mtg! を参照してください。

# 他の属性に基づいていくつかの新しい属性を計算します:
@mutate_node!(mtg, x = length(node_id(node)), y = node.x + 2, z = sum(node.y))

# 括弧なしでも使用できます:

@mutate_node! mtg x = length(node_id(node))
```
