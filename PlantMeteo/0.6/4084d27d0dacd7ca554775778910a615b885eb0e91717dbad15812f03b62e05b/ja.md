```
OpenMeteoUnits(temperature_unit, windspeed_unit, precipitation_unit)
OpenMeteoUnits(;temperature_unit="celsius", windspeed_unit="ms", precipitation_unit="mm")
```

APIを呼び出す際に使用される変数の単位を定義する型です。[open-meteo.com](https://open-meteo.com/) API。

# 引数

  * `temperature_unit`: 温度単位で、"celsius" または "fahrenheit" を指定できます。デフォルトは "celsius" です。
  * `windspeed_unit`: 風速単位で、"ms"、"kmh"、"mph"、または "kn" を指定できます。デフォルトは "ms" です。
  * `precipitation_unit`: 降水単位で、"mm" または "inch" を指定できます。デフォルトは "mm" です。

# 例

```jldoctest
julia> units = OpenMeteoUnits("celsius", "ms", "mm")
OpenMeteoUnits("celsius", "ms", "mm")
```
