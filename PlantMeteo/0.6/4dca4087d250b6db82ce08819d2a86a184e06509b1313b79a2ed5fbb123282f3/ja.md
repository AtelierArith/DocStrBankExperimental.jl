```
vapor_pressure(Tₐ, Rh; check=true)
```

与えられた温度 (°C) と相対湿度 (0-1) における蒸気圧 (kPa)。

# 引数

  * `Tₐ` (摂氏度): 空気温度
  * `Rh` (0-1): 相対湿度
  * `check` (Bool): true の場合、`Rh` が 0 と 1 の間であることを確認する

# 例

```julia
vapor_pressure(25.0, 0.4)
```
