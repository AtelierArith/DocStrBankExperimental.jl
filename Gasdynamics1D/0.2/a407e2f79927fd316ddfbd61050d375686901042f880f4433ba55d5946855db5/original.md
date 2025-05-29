```
Density(ρ0::StagnationDensity,M::MachNumber,Isentropic[;gas=Air])
```

Compute the density corresponding to stagnation density `ρ0` and Mach number `M`, using

$\rho = \rho_0 \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{-1/(\gamma-1)}$
