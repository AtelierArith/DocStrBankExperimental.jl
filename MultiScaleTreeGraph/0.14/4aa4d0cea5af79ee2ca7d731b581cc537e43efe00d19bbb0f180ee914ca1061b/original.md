```
MetaGraph(g::Node)
```

Convert an MTG into a [MetaGraph](https://juliagraphs.org/MetaGraphsNext.jl/dev/).

# Examples

```julia
# Importing an mtg from the package:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

MetaGraph(mtg)
```
