```
Temperature(T0::StagnationTemperature,M::MachNumber,Isentropic[;gas=Air])
```

Compute the temperature corresponding to stagnation temperature `T0` and Mach number `M`, using

$T = T_0 \left( 1 + \dfrac{\gamma-1}{2} M^2\right)^{-1}$

Can also omit the `Isentropic` argument, `Temperature(T0,M)`.
