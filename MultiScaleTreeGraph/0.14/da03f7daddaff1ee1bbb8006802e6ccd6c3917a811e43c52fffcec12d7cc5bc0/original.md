Print a node to io using an UTF-8 formatted representation of the `tree`. Most of the code from [DataTrees.jl](https://github.com/vh-d/DataTrees.jl/blob/master/src/printing.jl)

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
mtg
# / 1: $
# └─ / 2: Individual
#    └─ / 3: Axis
#       └─ / 4: Internode
#          ├─ + 5: Leaf
#          └─ < 6: Internode
#             └─ + 7: Leaf
```
