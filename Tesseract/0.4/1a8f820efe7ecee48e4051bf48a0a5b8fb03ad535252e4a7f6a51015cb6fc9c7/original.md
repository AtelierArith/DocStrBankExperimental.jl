```
mutable struct TessOutput{T}
    result::Union{T, Nothing}
end
```

Output object returned when adding an output renderer to a pipeline.  This object usually holds `nothing` until the [`tess_run_pipeline`](@ref) method completes.

See slso: [`tess_pipeline_text`](@ref)
