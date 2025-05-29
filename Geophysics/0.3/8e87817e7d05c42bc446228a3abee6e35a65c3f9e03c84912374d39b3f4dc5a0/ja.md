```
sonicspeed(T::Real,G::AbstractMole) = sqrt(gasconstant(G)*heatratio(T,G)*T)
```

理想気体の等エントロピー条件下における音波の擾乱速度 (m⋅s⁻¹ または ft⋅s⁻¹)。
