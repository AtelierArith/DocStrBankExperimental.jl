```
TargetColor(alpha::Float64)
```

Sets link colors depending on the color of their target node and an alpha level.

## Example

```julia
using CairoMakie, SankeyMakie
connections = [(1, 2, 10), (1, 3, 15), (3, 4, 5)]
labels = ["A", "B", "C", "D"]
colors = Makie.to_colormap(:tab20)
sankey(
    connections; 
    nodelabels = labels,
    nodecolor = colors[1:length(labels)],
    linkcolor = SankeyMakie.TargetColor(0.2),
)
```
