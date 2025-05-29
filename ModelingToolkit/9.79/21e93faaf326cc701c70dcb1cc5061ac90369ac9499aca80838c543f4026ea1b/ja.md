```julia
convert_system(
    ::Type{<:ModelingToolkit.ODESystem},
    sys,
    t;
    name
) -> ModelingToolkit.ODESystem

```

`NonlinearSystem`を`ODESystem`に変換するか、`ODESystem`を異なる独立変数を持つ新しい`ODESystem`に変換します。
