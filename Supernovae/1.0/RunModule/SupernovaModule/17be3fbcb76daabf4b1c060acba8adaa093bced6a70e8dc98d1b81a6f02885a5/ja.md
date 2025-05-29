```
mutable struct Supernova
```

超新星

# フィールド

  * `name::String`: 超新星の名前
  * `zeropoint::typeof(1.0u"AB_mag")`: 超新星のゼロポイント
  * `redshift::Float64`: 超新星の赤方偏移
  * `lightcurve::[`Lightcurve`](@ref)`: 超新星の光度曲線
