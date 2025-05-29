```
enthalpy(DryAir, T, P[, out_unit=u"m^3/kg"])
enthalpy(Vapor, T[, out_unit=u"m^3/kg"])
enthalpy(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

気体の比エンタルピーを計算します。湿った空気の場合、湿度を指定するパラメータを追加する必要があり、特性は気体の質量ではなく乾燥空気の質量に基づいています（`DryAir`や`Vapor`の場合と同様です）。

`Unitful`単位が使用されている場合、関数のすべてのパラメータ（無次元を除く）には単位が関連付けられている必要があります。単位が提供されていない場合、すべてのパラメータはSI単位を使用する必要があります（戻り値の型も同様です）。詳細については、`Psychro`モジュールのドキュメントを参照してください。

温度は`173.15 K < T < 473.15`の範囲で、圧力は5 MPa未満である必要があります。

# 例

```julia-repl
julia> enthalpy(DryAir, 293.15, 101325.0)
20121.2722813185

julia> enthalpy(DryAir, 20.0u"°C", 1.0u"atm")
20121.2722813185 kg^-1 J

julia> enthalpy(Vapor, 293.15)
2.5374003352412493e6

julia> enthalpy(Vapor, 20.0u"°C")
2.5374003352412493e6 kg^-1 J

julia> enthalpy(MoistAir, 293.15, RelHum, 0.7, 101325.0)
46142.773129687484

julia> enthalpy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
50944.84575377501 kg^-1 J

julia> enthalpy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"J/lb")
23108.193324739244 J lb^-1

```
