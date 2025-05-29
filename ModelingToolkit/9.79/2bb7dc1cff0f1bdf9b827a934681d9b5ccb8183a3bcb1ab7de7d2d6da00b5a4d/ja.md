```julia
independent_variables(
    sys::ModelingToolkit.AbstractSystem
) -> Vector{SymbolicUtils.BasicSymbolic{Real}}

```

システム `sys` の独立変数を取得します。

関連情報として [`@independent_variables`](@ref) と [`ModelingToolkit.get_iv`](@ref) を参照してください。
