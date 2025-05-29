```
StagnationPressure(p::Pressure,M::MachNumber,Isentropic[;gas=Air])
```

Compute the stagnation pressure corresponding to pressure `p` and Mach number `M`, using

$p_0 = p \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{\gamma/(\gamma-1)}$

Can also omit the `Isentropic` argument, `StagnationTemperature(T,M)`.
