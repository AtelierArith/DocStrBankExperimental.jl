```julia
open_loop(
    sys,
    ap::Union{Symbol, ModelingToolkit.AnalysisPoint};
    system_modifier
) -> Tuple{Any, Tuple{Any, Any}}

```

Apply `LoopTransferTransform` to the analysis point `ap` and return the result of `apply_transformation`.

# Keyword Arguments

  * `system_modifier`: a function which takes the modified system and returns a new system with any required further modifications performed.
