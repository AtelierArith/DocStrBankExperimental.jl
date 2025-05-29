```
epgRotation!(E::EPGStates, alpha::Float64, phi::Float64=0.0)
```

は、EPG状態のセットに対してBloch回転（<=> RFパルス）を適用します。

# 引数

  * `E::EPGStates``
  * `alpha::Float64`           - RFパルスのフリップ角（ラジアン）
  * `phi::Float64=0.0`         - RFパルスの位相（ラジアン）
