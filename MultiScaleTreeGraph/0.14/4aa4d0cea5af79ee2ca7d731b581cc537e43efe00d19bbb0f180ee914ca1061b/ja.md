```
MetaGraph(g::Node)
```

MTGを[MetaGraph](https://juliagraphs.org/MetaGraphsNext.jl/dev/)に変換します。

# 例

```julia
# パッケージからmtgをインポートする:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

MetaGraph(mtg)
```
