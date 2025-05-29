```
vpd_from_e(e,Tₐ)
```

空気の水蒸気圧 (kPa) と温度 (°C) から蒸気圧欠損 (kPa) を計算します。

計算は単純に vpd = eₛ - e を使用します。

# 例

```julia
vpd_from_e(1.5,25.0)
```
