```
SimpleAtmosphere{<:Number,<:StabilityClass}(kwargs...)<:Atmosphere
```

大気の簡単なモデル。

# 引数

  * `pressure::Number=101325`: 大気圧, Pa
  * `temperature::Number=298.15`: 周囲の温度, K
  * `windspeed::Number=1.5`: 風速, m/s
  * `windspeed_height::Number=10`: 風速計の高さ, m
  * `rel_humidity::Number=0`: 相対湿度, %
  * `stability::StabilityClass=ClassF`: パスキル-ギフォード安定性クラス
