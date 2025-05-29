```julia
initialization_equations(
    sys::ModelingToolkit.AbstractSystem
) -> Any

```

システム `sys` とそのサブシステムの初期化方程式を取得します。

関連情報として [`guesses`](@ref), [`defaults`](@ref), [`parameter_dependencies`](@ref) および [`ModelingToolkit.get_initialization_eqs`](@ref) を参照してください。
