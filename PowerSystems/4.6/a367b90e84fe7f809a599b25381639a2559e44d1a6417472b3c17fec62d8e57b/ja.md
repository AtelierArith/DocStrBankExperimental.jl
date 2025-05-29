```julia
ACBus(
    number,
    name,
    bustype::String,
    angle,
    voltage,
    voltage_limits,
    base_voltage,
    area,
    load_zone;
    ext
) -> PowerSystems.ACBus

```

レガシーコードのために文字列として指定されたバスタイプでの構築を許可します。
