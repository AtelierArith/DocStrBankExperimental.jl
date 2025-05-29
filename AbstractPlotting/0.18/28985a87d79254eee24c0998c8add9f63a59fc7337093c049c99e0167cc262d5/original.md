```
showgradients(
    cgrads::AbstractVector{Symbol};
    h = 0.0, offset = 0.2, textsize = 0.7,
    resolution = (800, length(cgrads) * 84)
)::Scene
```

Plots the given colour gradients arranged as horizontal colourbars. If you change the offsets or the font size, you may need to change the resolution.
