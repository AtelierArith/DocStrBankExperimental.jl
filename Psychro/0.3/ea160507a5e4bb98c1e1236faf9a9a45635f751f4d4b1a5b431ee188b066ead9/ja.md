```
volumem(DryAir, T, P[, out_unit=u"m^3/kg"])
volumem(Vapor, T[, out_unit=u"m^3/kg"])
volumem(MoistAir, T, HumidityType, hum, P[, out_unit="m^3/kg"])
```

気体のモル体積を計算します。湿った空気の場合、湿度を指定するパラメータを追加する必要があります。

`Unitful` 単位が使用されている場合、関数のすべてのパラメータ（無次元を除く）には単位が関連付けられている必要があります。単位が提供されていない場合、すべてのパラメータはSI単位を使用する必要があります（戻り値の型も同様です）。詳細については、`Psychro` モジュールのドキュメントを参照してください。

温度は `173.15 K < T < 473.15` の範囲で、圧力は5 MPa未満である必要があります。

# 例

```julia-repl
julia> volumem(DryAir, 293.15, 101325.0)
0.024046522993685877

julia> volumem(DryAir, 20.0u"°C", 1.0u"atm")
0.024046522993685877 m^3 mol^-1

julia> volumem(Vapor, 293.15)
1.040831369053248

julia> volumem(Vapor, 20.0u"°C")
1.040831369053248 m^3 mol^-1

julia> volumem(MoistAir, 293.15, RelHum, 0.7, 101325.0)
0.02404547233948706

julia> volumem(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm")
0.024045209859305458 m^3 mol^-1

julia> volumem(MoistAir, 20.0u"°C", WetBulb, 18.0u"°C", 1.0u"atm", u"inch^3/mol")
1467.32873315839 in^3 mol^-1
```
