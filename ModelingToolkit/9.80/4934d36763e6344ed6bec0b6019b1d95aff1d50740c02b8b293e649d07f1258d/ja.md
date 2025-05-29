```julia
defaults(sys::ModelingToolkit.AbstractSystem) -> Any

```

システム sys とそのサブシステムのデフォルト値を取得します。明示的に提供されていない場合、変数とパラメータはこれらの値に初期化されます。

関連情報として [`initialization_equations`](@ref)、[`parameter_dependencies`](@ref)、および [`ModelingToolkit.get_defaults`](@ref) を参照してください。
