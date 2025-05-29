```
get_named_looptransfer(sys, ap::AnalysisPoint; kwargs...)
get_named_looptransfer(sys, ap_name::Symbol; kwargs...)
```

Call [`ModelingToolkitStandardLibrary.Blocks.get_looptransfer`](@ref) while retaining signal names. Returns a `NamedStateSpace` object (similar to [`named_ss`](@ref)).
