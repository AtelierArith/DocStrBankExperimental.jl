```julia
with_units_base(
    f::Function,
    sys::PowerSystems.System,
    units::Union{InfrastructureSystems.UnitSystemModule.UnitSystem, String}
) -> Any

```

指定された値に[`System`](@ref)の[単位基準](@ref per_unit)を設定し、関数を実行し、その後単位基準を元に戻す「コンテキストマネージャ」。

# 例

```julia
active_power_mw = with_units_base(sys, UnitSystem.NATURAL_UNITS) do
    get_active_power(gen)
end
# 現在、active_power_mwはシステムの単位基準が何であれ自然単位で表されます
```
