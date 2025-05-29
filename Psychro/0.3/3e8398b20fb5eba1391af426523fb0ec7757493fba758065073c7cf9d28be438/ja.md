```
volume(DryAir, T, P[, out_unit=u"m^3/kg"])
volume(Vapor, T[, out_unit=u"m^3/kg"])
volume(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

気体の比体積を計算します。湿った空気の場合、湿度を指定するパラメータを追加する必要があり、特性は気体の質量ではなく乾燥空気の質量に基づいています（`DryAir`や`Vapor`の場合と同様です）。

`Unitful`単位が使用されている場合、関数のすべてのパラメータ（無次元を除く）には単位が関連付けられている必要があります。単位が提供されていない場合、すべてのパラメータはSI単位を使用する必要があります（戻り値の型も同様です）。詳細については、`Psychro`モジュールのドキュメントを参照してください。

温度は`173.15 K < T < 473.15`の範囲で、圧力は5 MPa未満である必要があります。

# 例

```julia-repl
julia> volume(DryAir, 293.15, 101325.0)
0.8302353995092402

julia> volume(DryAir, 20.0u"°C", 1.0u"atm")
0.8302353995092402 kg^-1 m^3

julia> volume(Vapor, 293.15)
57.77492045936827

julia> volume(Vapor, 20.0u"°C")
57.77492045936827 kg^-1 m^3

julia> volume(MoistAir, 293.15, RelHum, 0.7, 101325.0)
0.843889817602806

julia> volume(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
0.8464079202783964 kg^-1 m^3

julia> volume(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"inch^3/lb")
23428.490579267214 in^3 lb^-1
```
