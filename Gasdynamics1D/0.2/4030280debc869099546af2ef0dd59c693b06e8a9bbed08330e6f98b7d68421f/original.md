```
StagnationTemperature(T::Temperature,M::MachNumber,Isentropic[;gas=Air])
```

Compute the stagnation temperature corresponding to temperature `T` and Mach number `M`, using

$T_0 = T \left( 1 + \dfrac{\gamma-1}{2} M^2\right)$

Can also omit the `Isentropic` argument, `StagnationTemperature(T,M)`.
