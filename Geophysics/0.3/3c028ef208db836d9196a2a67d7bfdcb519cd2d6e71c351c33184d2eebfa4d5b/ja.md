```
specificenergy(T::Real,G::AbstractMole) = heatvolume(T,G)*T
```

理想気体の比エネルギー `e` は `specificenthalpy(T,G)-gasconstant(G)*T` です (J⋅kg⁻¹ または ft⋅lb⋅slug⁻¹)。
