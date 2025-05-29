```julia
check_components(
    sys::PowerSystems.System,
    ::Type{T<:PowerSystems.Component};
    check_masked_components
)

```

与えられた抽象または具体的な型のコンポーネントの値をチェックします。スローされる例外については、[`check_component`](@ref)を参照してください。
