```
get_named_comp_sensitivity(sys, ap::AnalysisPoint; kwargs...)
get_named_comp_sensitivity(sys, ap_name::Symbol; kwargs...)
```

Call [`ModelingToolkitStandardLibrary.Blocks.get_comp_sensitivity`](@ref) while retaining signal names. Returns a `NamedStateSpace` object (similar to [`named_ss`](@ref)).
