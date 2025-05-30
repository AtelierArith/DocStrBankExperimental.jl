```
RadialCharacteristics <: AbstractStaticCharacteristics
```

Stores the values for the calculation of $m ~ exp( -||M (x - xₛ)||^{2ν} )$

`scaling` : m ∈ [0, 1]

`power` : ν ∈ [0, ∞)

`center` : xₛ ∈ R^{3}

`curvature` : M ∈ R^{3 x 3} for the planar boundaries
