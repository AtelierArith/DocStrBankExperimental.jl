```julia
unknowns(sys::ModelingToolkit.AbstractSystem) -> Any

```

システム `sys` とそのサブシステムの未知の変数を取得します。これらは `observables(sys)` とは異なり、明示的に解決する必要があります。

関連情報として [`ModelingToolkit.get_unknowns`](@ref) を参照してください。
