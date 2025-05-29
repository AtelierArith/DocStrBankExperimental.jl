```julia
set_units_base_system!(
    system::PowerSystems.System,
    units::Union{InfrastructureSystems.UnitSystemModule.UnitSystem, String}
)

```

デバイスのゲッタ関数の単位ベースを設定します。すべてのゲッタ関数の動作を変更します。

# 例

```julia
set_units_base_system!(sys, "NATURAL_UNITS")
```

```julia
set_units_base_system!(sys, UnitSystem.SYSTEM_BASE)
```
