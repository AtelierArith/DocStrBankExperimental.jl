```
get_named_sensitivity(sys, ap::AnalysisPoint; kwargs...)
get_named_sensitivity(sys, ap_name::Symbol; kwargs...)
```

信号名を保持しながら [`ModelingToolkitStandardLibrary.Blocks.get_sensitivity`](@ref) を呼び出します。`NamedStateSpace` オブジェクトを返します（[`named_ss`](@ref) に似ています）。
