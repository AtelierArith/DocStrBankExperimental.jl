```
Popout(T)
```

Create an HTML widget wrapping the widget `T` and showing it either on hover or upon click.

This is useful to generat widgets to be used with [`StructBond`](@ref) for custom fields whose types are custom Types.

The convenience function [`popoutwrap`](@ref) can be used to directly create a `Popup` of a `StructBond{T}` to facilitate nested `StructBond` views.

See also: [`BondTable`](@ref), [`StructBond`](@ref), [`popoutwrap`](@ref), [`@fieldbond`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
