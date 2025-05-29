```
plotrg(r::AbstractMatrix)
plotrg!(ax::Axis, r::AbstractMatrix)
```

Correlation plot of matrix `r`.

# Keyword arguments

```
circle          whether to draw cicles instead of rectangles; default true
diagonal        whether to visualize diagonal elements; default false
colormap        colormap of values; default :RdBu_10
colorrange      start and end points of colormap; default (-1, 1)
strokewidth     width of outline around surrounding boxes; default 0.5
```
