```julia
get_max_reactive_power(d::PowerSystems.RenewableGen) -> Any

```

再生可能エネルギーの最大無効電力を、`rating` * sin(acos(`power_factor`))として計算して返します。
