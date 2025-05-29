```
Categorical(colormaplike)
```

Accepts all colormap values that the `colormap` attribute of a plot accepts. Will make sure to map one value to one color and create the correct Colorbar for the plot.

Example:

```julia
fig, ax, pl = barplot(1:3; color=1:3, colormap=Makie.Categorical(:viridis))
```

!!! warning
    This feature might change outside breaking releases, since the API is not yet finalized

