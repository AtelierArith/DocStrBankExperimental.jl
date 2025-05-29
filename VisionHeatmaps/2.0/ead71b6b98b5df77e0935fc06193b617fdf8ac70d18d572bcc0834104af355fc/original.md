```
heatmap(expl::Explanation)
heatmap(expl::Explanation, pipeline)
heatmap(expl::Explanation, image)   
heatmap(expl::Explanation, image, pipeline)
```

Visualize `Explanation` from XAIBase as a vision heatmap. Assumes WHCN convention (width, height, channels, batch dimension) for `explanation.val`. This will use the default heatmapping style for the given type of explanation.
