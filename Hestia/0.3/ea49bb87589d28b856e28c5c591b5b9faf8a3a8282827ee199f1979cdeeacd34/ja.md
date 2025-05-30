```
RadialCharacteristics <: AbstractStaticCharacteristics
```

$$
m ~ exp( -||M (x - xₛ)||^{2ν} )
$$

の計算のための値を格納します。

`scaling` : m ∈ [0, 1]

`power` : ν ∈ [0, ∞)

`center` : xₛ ∈ R^{3}

`curvature` : M ∈ R^{3 x 3} 平面境界のための
