```
prune!(node)
```

`node`でツリーを剪定します。*すなわち*、`node`（それ自体を含む）から始まる全てのサブツリーを削除します。

ノードがルートである場合、または（削除された）ノードの親ノードである場合はエラーを返します。

# 例

```julia
using MultiScaleTreeGraph
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

prune!(get_node(mtg, 6))

mtg
```
