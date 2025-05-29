```
flowerplot!(ax, bm)
flowerplot(bm)
```

Plot the network with nodes positioned in circles according to the blockmodel groups. The first group is placed in the center.

# Attributes

  * `edgecolor = :grey70`
  * `edgewidth = 1`
  * `nodecolor = :black`
  * `showlabels = true`
  * `radii = fill(1, length(bm.labels))`
  * `args...` further arguments are passed to `Makie.scatter`
