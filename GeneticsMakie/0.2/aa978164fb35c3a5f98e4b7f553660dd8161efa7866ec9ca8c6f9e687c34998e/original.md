```
plotld(LD::AbstractMatrix; kwargs)
plotld!(ax::Axis, LD::AbstractMatrix; kwargs)
```

Heatmap of symmetric correlation matrix `LD` with the diagonal elements on the x-axis.

# Keyword arguments

```
threshold       threshold below which values are ignored; default 1/9
colormap        colormap of values; default cgrad(:Blues_9, 9, categorical = true)
colorrange      start and end points of colormap; default (0, 1)
strokewidth     width of outline around heatmap boxes; default 0
```
