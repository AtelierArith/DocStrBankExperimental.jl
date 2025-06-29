```
Explanation(val, output, output_selection, analyzer, heatmap, extras)
```

Return type of analyzers when calling [`analyze`](@ref).

## Fields

  * `val`: numerical output of the analyzer, e.g. an attribution or gradient
  * `output`: model output for the given analyzer input
  * `output_selection`: index of the output used for the explanation
  * `analyzer`: symbol corresponding the used analyzer, e.g. `:Gradient` or `:LRP`
  * `heatmap`: symbol indicating a preset heatmapping style,   e.g. `:attribution`, `:sensitivity` or `:cam`
  * `extras`: optional named tuple that can be used by analyzers   to return additional information.
