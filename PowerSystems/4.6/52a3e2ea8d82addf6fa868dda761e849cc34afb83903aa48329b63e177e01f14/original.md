```julia
get_dynamic_components(
    device::PowerSystems.DynamicInjection
) -> Base.Generator{I, F} where {I<:(Base.Iterators.Filter{PowerSystems.var"#6#8", I} where I<:(Base.Iterators.Zip{Is} where Is<:Tuple{Any, Tuple})), F<:(PowerSystems.var"#5#7"{<:PowerSystems.DynamicInjection})}

```

Return all the dynamic components of a [`DynamicInjection`](@ref) device
