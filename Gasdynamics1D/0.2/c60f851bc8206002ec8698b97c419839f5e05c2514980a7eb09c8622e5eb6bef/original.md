```
MachNumber(T_over_T0::TemperatureRatio,Isentropic[;gas=Air])
```

Compute the Mach number corresponding to the ratio of temperature to stagnation temperature `T_over_T0`, using

$M = \left( \dfrac{2}{\gamma-1}\left(\dfrac{1}{T/T_0} - 1 \right)\right)^{1/2}$

Can also omit the `Isentropic` argument, `MachNumber(T_over_T0)`. Can also  supply the arguments for `T` and `T0` separately, `MachNumber(T,T0)`
