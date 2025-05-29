```
entropym(DryAir, T, P[, out_unit=u"m^3/kg"])
entropym(Vapor, T[, out_unit=u"m^3/kg"])
entropym(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

気体のモルエントロピーを計算します。湿った空気の場合、湿度を指定するパラメータを追加する必要があります。

`Unitful` 単位が使用されている場合、関数のすべてのパラメータ（無次元を除く）には単位が関連付けられている必要があります。単位が提供されていない場合、すべてのパラメータはSI単位を使用する必要があります（戻り値の型も同様です）。詳細については、`Psychro` モジュールのドキュメントを参照してください。

温度は `173.15 K < T < 473.15` の範囲で、圧力は5 MPa未満である必要があります。

# 例

```julia-repl
julia> entropym(DryAir, 293.15, 101325.0)
2.0590912665460226

julia> entropym(DryAir, 20.0u"°C", 1.0u"atm")
2.0590912665460226 J K^-1 mol^-1

julia> entropy(Vapor, 293.15)
8665.873003613997

julia> entropym(Vapor, 20.0u"°C")
156.11812860454717 J K^-1 mol^-1

julia> entropym(MoistAir, 293.15, RelHum, 0.7, 101325.0)
4.739496639035868

julia> entropym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
5.197949865380578 J K^-1 mol^-1

julia> entropym(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"kJ/kmol/°F")
2.8877499252114327 °F^-1 kJ kmol^-1

```
