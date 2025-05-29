```julia
observed(sys::ModelingToolkit.AbstractSystem) -> Any

```

システム `sys` とそのサブシステムの観測方程式を取得します。これらは `unknowns(sys)` に基づいて表現でき、明示的に解決する必要はありません。

[`observables`](@ref) および [`ModelingToolkit.get_observed()`](@ref) も参照してください。
