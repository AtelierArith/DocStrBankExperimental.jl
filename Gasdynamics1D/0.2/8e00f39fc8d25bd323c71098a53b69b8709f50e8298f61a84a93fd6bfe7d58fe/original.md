```
    T0OverT(M::MachNumber,Isentropic[;gas=PerfectGas]) -> TemperatureRatio
```

Compute the ratio of stagnation temperature to temperature for Mach number `M`.

$\dfrac{T_0}{T} = 1 + \dfrac{\gamma-1}{2}M^2$

Can also omit the `Isentropic` argument, `T0OverT(M)`
