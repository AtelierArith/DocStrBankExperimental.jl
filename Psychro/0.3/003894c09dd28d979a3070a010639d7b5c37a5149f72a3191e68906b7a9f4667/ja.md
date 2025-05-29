# 湿った空気、乾燥した空気、飽和水蒸気の熱力学的特性

以下のメソッドは、湿った空気の熱力学的特性を計算します：

```
volume(MoistAir, T, HumidityType, humidity, P[, outunit]) 
volume(MoistAir, T, HumidityType, humidity, P[, outunit]) 
density(MoistAir, T, HumidityType, humidity, P[, outunit])
enthalpy(MoistAir, T, HumidityType, humidity, P[, outunit])
enthalpym(MoistAir, T, HumidityType, humidity, P[, outunit])
entropy(MoistAir, T, HumidityType, humidity, P[, outunit])
entropym(MoistAir, T, HumidityType, humidity, P[, outunit])
compressfactor(MoistAir, T, HumidityType, humidity, P[, outunit])
dewpoint(MoistAir, T, HumidityType, humidity, P[, outunit]) 
wetbulb(MoistAir, T, HumidityType, humidity, P[, outunit]) 
humrat(MoistAir, T, HumidityType, humidity, P) 
relhum(MoistAir, T, HumidityType, humidity, P) 
humrat(MoistAir, T, HumidityType, humidity, P) 
spechum(MoistAir, T, HumidityType, humidity, P) 
molarfrac(MoistAir, T, HumidityType, humidity, P)
```

上記のメソッドは、湿った空気の以下の熱力学的特性を計算します：

  * `volume` 比容積
  * `volumem` モル体積
  * `density` 密度
  * `enthalpy` 比エンタルピー
  * `enthalpym` モルエンタルピー
  * `entropy` 比エントロピー
  * `entropym` モルエントロピー
  * `compressfactor` 圧縮因子 Z
  * `dewpoint` 露点温度
  * `wetbulb` アディアバティック飽和温度
  * `humrat` 湿度比
  * `relhum` 相対湿度
  * `spechum` 比湿
  * `molarfrac` 水蒸気のモル分率

湿度は、以下の2つのパラメータを使用して指定されます：

  * 湿度の指定方法
  * 湿度の実際の値

湿度を特徴付けるために、以下のタイプが使用されます。

  * `WetBulb` 湿球温度、実際にはアディアバティック飽和温度
  * `DewPoint` 露点温度
  * `RelHum` 相対湿度
  * `HumRat` 湿度比（kgの蒸気 / kgの乾燥空気）
  * `SpecHum` 比湿（kgの蒸気 / kgの湿った空気）
  * `MolarFrac` 水蒸気のモル分率

# 例

```julia-repl
julia> volume(MoistAir, 293.15, WetBulb, 291.15, 101325.0)
0.8464079202783964

julia> volume(MoistAir, 293.15, DewPoint, 291.15, 101325.0)
0.8475219875187474

julia> volume(MoistAir, 293.15, RelHum, 0.7, 101325.0)
0.843889817602806

julia> volume(MoistAir, 20.0u"°C", DewPoint, 60.0u"°F", 1.0u"atm")
0.8449934929585231 kg^-1 m^3

julia> volumem(MoistAir, 293.15, RelHum, 0.5, 93000.0)
0.026199080086890276

julia> volumem(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa", u"inch^3/kmol")
1.598733210336603e6 in^3 kmol^-1

julia> density(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa")
1.0976075893895811 kg m^-3

julia> density(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa", u"lb/inch^3")
3.965358988338535e-5 in^-3 lb

julia> volumem(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa", u"inch^3/kmol")
1.598733210336603e6 in^3 kmol^-1

julia> enthalpy(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa")
50667.43014746832 kg^-1 J

julia> enthalpym(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa")
1439.6551689935861 J mol^-1

julia> compressfactor(MoistAir, -90.0u"°C", RelHum, 0.01, 4.5u"MPa")
0.8552758629097985

julia> wetbulb(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa", u"°C")
17.0 °C

julia> dewpoint(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa", u"°C")
15.475836053510477 °C

julia> humrat(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa")
0.012032930694441925

julia> relhum(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa")
0.7517801524436909

julia> spechum(MoistAir, 20.0u"°C", WetBulb, 17.0u"°C", 93u"kPa")
0.011889860823189923
```
