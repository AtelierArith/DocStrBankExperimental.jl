```
heatmap(x::AbstractArray)
heatmap(x::AbstractArray, pipeline)
heatmap(x::AbstractArray, image)
heatmap(x::AbstractArray, image, pipeline)
```

Visualize 4D arrays as heatmaps, assuming the WHCN convention for input array dimensions (width, height, color channels, batch dimension).
