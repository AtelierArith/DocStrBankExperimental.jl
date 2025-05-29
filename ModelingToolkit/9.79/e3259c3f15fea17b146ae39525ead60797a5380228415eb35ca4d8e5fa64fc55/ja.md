```julia
parameter_dependencies(
    sys::ModelingToolkit.AbstractSystem
) -> Any

```

システム `sys` とそのサブシステムのパラメータ依存関係を取得します。

[`defaults`](@ref) および [`ModelingToolkit.get_parameter_dependencies`](@ref) も参照してください。
