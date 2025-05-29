```
heatpressure(T::Real,G::AbstractMole) = heatvolume(T,G)+gasconstant(G)
```

理想気体の定圧における比熱 `cₚ` (J⋅kg⁻¹⋅K⁻¹ または ft⋅lb⋅slug⁻¹⋅°R⁻¹)。
