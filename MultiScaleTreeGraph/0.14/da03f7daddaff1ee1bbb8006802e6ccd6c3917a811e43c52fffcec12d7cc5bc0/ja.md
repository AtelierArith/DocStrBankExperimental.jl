ノードをUTF-8形式の`tree`の表現を使用してioに印刷します。[DataTrees.jl](https://github.com/vh-d/DataTrees.jl/blob/master/src/printing.jl)からのほとんどのコード

# 例

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
