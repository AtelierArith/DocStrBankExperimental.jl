```
compressfactor(DryAir, T, P[, out_unit=u"m^3/kg"])
compressfactor(Vapor, T[, out_unit=u"m^3/kg"])
compressfactor(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

気体の圧縮因子 Z を計算します。湿った空気の場合、湿度を指定するパラメータを追加する必要があります。

`Unitful` 単位が使用されている場合、関数のすべてのパラメータ（無次元を除く）には単位が関連付けられている必要があります。単位が提供されていない場合、すべてのパラメータは SI 単位を使用する必要があります（戻り値の型も同様です）。詳細については、`Psychro` モジュールのドキュメントを参照してください。

温度は `173.15 K < T < 473.15` の範囲で、圧力は 5 MPa 未満である必要があります。

# 例

```julia-repl
julia> compressfactor(DryAir, 293.15, 101325.0)
1.2044776705391136

julia> compressfactor(DryAir, 20.0u"°C", 1.0u"atm")
1.2044776705391136 kg m^-3

julia> compressfactor(Vapor, 293.15)
0.017308548277505224

julia> compressfactor(Vapor, 20.0u"°C")
0.017308548277505224 kg m^-3

julia> compressfactor(MoistAir, 293.15, RelHum, 0.7, 101325.0)
1.1971436091840653

julia> compressfactor(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
1.195819185774941 kg m^-3

```
