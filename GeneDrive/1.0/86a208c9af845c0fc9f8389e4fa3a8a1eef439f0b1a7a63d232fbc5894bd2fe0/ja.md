```
mutable struct EggDurationRossi <: TemperatureResponse
    a::Float64
    b::Float64
    c::Float64
    d::Float64
    e::Float64
    f::Float64
end
```

`q_temperature_response`のデータ。`Species`: AedesAegypti, `LifeStage`: 卵の段階。出典: Rossi et al (2014).
