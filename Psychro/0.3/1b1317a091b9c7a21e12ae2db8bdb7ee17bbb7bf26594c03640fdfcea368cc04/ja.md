```
entropy(DryAir, T, P[, out_unit=u"m^3/kg"])
entropy(Vapor, T[, out_unit=u"m^3/kg"])
entropy(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

気体の比エントロピーを計算します。湿った空気の場合、湿度を指定するパラメータを追加する必要があり、この特性は気体の質量ではなく乾燥空気の質量に基づいています（`DryAir`や`Vapor`の場合と同様です）。

`Unitful`単位が使用されている場合、関数のすべてのパラメータ（無次元を除く）には単位が関連付けられている必要があります。単位が提供されていない場合、すべてのパラメータはSI単位を使用する必要があります（戻り値の型も同様です）。詳細については、`Psychro`モジュールのドキュメントを参照してください。

温度は`173.15 K < T < 473.15`の範囲で、圧力は5 MPa未満である必要があります。

# 例

```julia-repl
julia> entropy(DryAir, 293.15, 101325.0)
71.09262577195514

julia> entropy(DryAir, 20.0u"°C", 1.0u"atm")
71.09262577195514 kg^-1 J K^-1

julia> entropy(Vapor, 293.15)
8665.873003613997

julia> entropy(Vapor, 20.0u"°C")
8665.873003613997 kg^-1 J K^-1

julia> entropy(MoistAir, 293.15, RelHum, 0.7, 101325.0)
166.33538729355692

julia> entropy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
182.97140931650105 kg^-1 J K^-1

julia> entropy(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"kJ/lb/°F")
0.04610801955228433 °F^-1 kJ lb^-1

```
