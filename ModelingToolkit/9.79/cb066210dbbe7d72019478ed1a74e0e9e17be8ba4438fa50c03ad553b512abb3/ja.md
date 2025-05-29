```julia
parameters(
    sys::ModelingToolkit.AbstractSystem;
    initial_parameters
) -> Vector{Any}

```

システム `sys` とそのサブシステムのパラメータを取得します。

関連情報として [`@parameters`](@ref) と [`ModelingToolkit.get_ps`](@ref) を参照してください。
