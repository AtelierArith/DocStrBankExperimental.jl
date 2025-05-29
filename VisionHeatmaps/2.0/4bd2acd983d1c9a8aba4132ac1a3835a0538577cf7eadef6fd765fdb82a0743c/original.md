```
heatmap(input::AbstractArray, analyzer::AbstractXAIMethod)
heatmap(input::AbstractArray, analyzer::AbstractXAIMethod, image)
```

Compute an `Explanation` for a given `input` using the XAI method `analyzer` and visualize it as a vision heatmap. This will use the default heatmapping style for the given type of explanation.
