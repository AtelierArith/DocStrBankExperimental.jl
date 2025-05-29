```
heatmap(expl::Explanation, text)
```

Visualize `Explanation` from XAIBase as text heatmap. Text should be a vector containing vectors of strings, one for each input in the batched explanation.

This will use the default heatmapping style for the given type of explanation. Defaults can be overridden via keyword arguments.
