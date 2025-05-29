```
Pressure(p0::StagnationPressure,M::MachNumber,Isentropic[;gas=Air])
```

Compute the pressure corresponding to stagnation pressure `p0` and Mach number `M`, using

$p = p_0 \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{-\gamma/(\gamma-1)}$

Can also omit the `Isentropic` argument, `Temperature(T0,M)`.
