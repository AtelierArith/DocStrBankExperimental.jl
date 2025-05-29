```julia
get_max_reactive_power(
    d::PowerSystems.RenewableDispatch
) -> Any

```

再生可能発電の最大無効電力を返します。無効電力制限が何も指定されていない場合、評価 * 力率として計算されます。
