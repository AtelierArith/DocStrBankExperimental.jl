```
get_node(node::Node, id::Int)
```

idでmtg内のノードを取得します。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
node_6_2 = get_node(mtg, 6)
```
