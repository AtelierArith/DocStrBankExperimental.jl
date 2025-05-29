Abstract super type of all XAI methods.

It is expected that all XAI methods are callable types that return an `Explanation`:

```julia
(method::AbstractXAIMethod)(input, output_selector::AbstractOutputSelector)
```

If this function is implemented, XAIBase will provide the `analyze` functionality and `heatmap` functionality by loading either VisionHeatmaps.jl or TextHeatmaps.jl.
