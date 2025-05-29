```
enthalpym(DryAir, T, P[, out_unit=u"m^3/kg"])
enthalpym(Vapor, T[, out_unit=u"m^3/kg"])
enthalpym(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

気体のモルエンタルピーを計算します。湿った空気の場合、湿度を指定するパラメータを追加する必要があります。

`Unitful` 単位が使用されている場合、関数のすべてのパラメータ（無次元を除く）には単位が関連付けられている必要があります。単位が提供されていない場合、すべてのパラメータはSI単位を使用する必要があります（戻り値の型も同様です）。詳細については、`Psychro` モジュールのドキュメントを参照してください。

温度は `173.15 K < T < 473.15` の範囲で、圧力は5 MPa未満である必要があります。

# 例

```julia-repl
julia> enthalpym(DryAir, 293.15, 101325.0)
582.7824697199684

julia> enthalpym(DryAir, 20.0u"°C", 1.0u"atm")
582.7824697199684 J mol^-1

julia> enthalpy(Vapor, 293.15)
2.5374003352412493e6

julia> enthalpym(Vapor, 20.0u"°C")
45711.977511464975 J mol^-1

julia> enthalpym(MoistAir, 293.15, RelHum, 0.7, 101325.0)
1314.7744549269437

julia> enthalpym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
1447.2684837312868 J mol^-1

julia> enthalpym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"kJ/kmol")
1447.2684837312868 kJ kmol^-1

```
