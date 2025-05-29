```
localizationsplot(localizations::Vector{Localizations}, color::Symbol)
localizationsplot(localizations::Vector{Vector{Localization}}, colors::Vector{Symbol})
```

Plot localizations by spatial coordinates. Assumes that the y-coordinate is inverted. Defaults to 0-to-40960 on each axis, but option may be specified using keyword arguments xlims=(x1, x2) and ylims=(y1, y2). Colors are specified in the documentation for Plots.jl. Can tune opacity with opacity= keword argument. factor= can be tuned for display in the pane or for saving and printing (recommended 4, default 1).
