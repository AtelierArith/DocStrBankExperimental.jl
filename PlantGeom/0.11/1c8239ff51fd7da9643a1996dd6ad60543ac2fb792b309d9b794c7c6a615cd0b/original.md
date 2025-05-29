```
colorbar(parent, plotobject, kwargs...)
```

Add a colorbar based on the attribute chose to color the plot. plotobject must be a plot of an MTG colored by an attribute. Use Makie.Colorbar for any other use case instead.

# Arguments

  * `parent`: parent scene
  * `plotobject`: plot object to add the colorbar to
  * `kwargs`: keyword arguments to pass to Makie.Colorbar, *e.g.* `label="Length (m)"`

# Example

```julia using GLMakie, MultiScaleTreeGraph, PlantGeom file = joinpath(dirname(dirname(pathof(PlantGeom))), "test", "files", "simple*plant.opf") opf = read*opf(file)

f, ax, p = viz(opf, color=:Length) colorbar(f[1, 2], p) f
