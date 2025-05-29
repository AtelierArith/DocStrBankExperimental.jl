```
edges(px [, Δx[, x0]])
```

Heatmap range transformation from pixel coordinates to physical coordinates, with pixelsize Δx and offset x0, both in physical units.

#### Examples:

```@docs
px = 1:5
Δx = 2.5
x0 = 2.5
edges(px)
 [0.5, 1.5, 2.5, 3.5, 4.5]

edges(px, Δx)
 [1.25, 3.75, 6.25, 8.75, 11.25]

edges(px, Δx, x0)
 [-1.25, 1.25, 3.75, 6.25, 8.75]
```
