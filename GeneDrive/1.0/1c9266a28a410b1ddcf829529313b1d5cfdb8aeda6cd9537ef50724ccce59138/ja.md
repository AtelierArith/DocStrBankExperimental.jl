```
mutable struct EggMortalityRossi <: TemperatureResponse
    a::Float64
    b::Float64
end
```

`μ_temperature_response`のデータ。`Species`: AedesAegypti, `LifeStage`: Egg。出典: Rossi et al (2014)。

# 引数

  * `a::Float64`: 低温での死亡率、検証範囲: `(0, nothing)`
  * `b::Float64`: 温度の影響因子、検証範囲: `(0, nothing)`
