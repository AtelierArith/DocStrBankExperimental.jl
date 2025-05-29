```julia
get_components(
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System;
    subsystem_name
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:PowerSystems.Component, I<:(Vector)}

```

指定された `Type` のコンポーネントのイテレータを [`System`](@ref) から返します。

`T` は具体的または抽象の [`Component`](@ref) タイプであり、[Type Tree](@ref) から取得できます。配列が必要な場合は、結果に対して collect を呼び出してください。

# 例

```julia
iter = get_components(ThermalStandard, sys)
iter = get_components(Generator, sys)
generators = collect(get_components(Generator, sys))
```

参照: [`iterate_components`](@ref), [`get_components` with a filter](@ref get_components(     filter_func::Function,     ::Type{T},     sys::System;     subsystem_name = nothing, ) where {T <: Component}), [`get_available_components`](@ref), [`get_buses`](@ref)
