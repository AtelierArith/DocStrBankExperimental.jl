```julia
get_components(
    filter_func::Function,
    ::Type{T<:PowerSystems.Component},
    sys::PowerSystems.System;
    subsystem_name
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:PowerSystems.Component, I<:(Vector)}

```

与えられた `Type` のコンポーネントのイテレータを [`System`](@ref) から返し、追加のフィルタを使用します。

`T` は具体的または抽象的な [`Component`](@ref) タイプであり、[Type Tree](@ref) から取得できます。配列が必要な場合は、結果に対して collect を呼び出してください。

# 例

```julia
iter_coal = get_components(x -> get_fuel(x) == ThermalFuels.COAL, Generator, sys)
pv_gens =
    collect(get_components(x -> get_prime_mover_type(x) == PrimeMovers.PVe, Generator, sys))
```

参照: [`get_components`](@ref get_components(     ::Type{T},     sys::System;     subsystem_name = nothing, ) where {T <: Component}), [`get_available_components`](@ref), [`get_buses`](@ref)
