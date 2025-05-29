```
mutable struct NoResponse <: TemperatureResponse
    baseline_value::Float64
end
```

温度応答なしのモデルのデータ。

# 引数:

  * `baseline_value::Float64`: 文献に基づく（動的に計算されるのではなく）重要な率パラメータ。
