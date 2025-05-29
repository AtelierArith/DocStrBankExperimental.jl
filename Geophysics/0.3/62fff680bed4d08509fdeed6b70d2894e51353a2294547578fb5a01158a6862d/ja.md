```
enthalpy(T::Real,G::AbstractMole) = heatpressure(T,G)*T
```

理想気体の比エンタルピー `h` は `specificenergy(T,G)+gasconstant(G)*T` (J⋅kg⁻¹ または ft⋅lb⋅slug⁻¹) です。
