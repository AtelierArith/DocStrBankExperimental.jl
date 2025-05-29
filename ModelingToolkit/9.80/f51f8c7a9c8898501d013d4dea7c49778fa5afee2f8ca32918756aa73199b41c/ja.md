```julia
guesses(sys::ModelingToolkit.AbstractSystem) -> Any

```

システム `sys` とそのサブシステムの初期化システムにおける変数の推測を取得します。

関連情報として [`initialization_equations`](@ref) と [`ModelingToolkit.get_guesses`](@ref) を参照してください。
