```
StagnationDensity(ρ::Density,M::MachNumber,Isentropic[;gas=Air])
```

Compute the stagnation density corresponding to density `ρ` and Mach number `M`, using

$\rho_0 = \rho \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{1/(\gamma-1)}$
