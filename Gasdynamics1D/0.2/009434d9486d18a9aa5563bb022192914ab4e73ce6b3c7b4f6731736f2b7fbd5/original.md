```
MachNumber(ρ_over_ρ0::DensityRatio,Isentropic[;gas=Air])
```

Compute the Mach number corresponding to the ratio of density to stagnation density `ρ_over_ρ0`, using

$M = \left( \dfrac{2}{\gamma-1}\left(\dfrac{1}{(\rho/\rho_0)^{(\gamma-1)}} - 1 \right)\right)^{1/2}$

Can also supply the arguments for `ρ` and `ρ0` separately, `MachNumber(ρ,ρ0)`
