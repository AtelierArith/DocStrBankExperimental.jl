```
P0OverP0Star(M::MachNumber,FannoFlow[;gas=PerfectGas]) -> StagnationPressureRatio
```

Compute the ratio of stagnation pressure to the sonic stagnation pressure in Fanno flow, given Mach number `M`, from

$\dfrac{p_0}{p_0^*} = \dfrac{1}{M} \left(\dfrac{2+(\gamma-1)M^2}{\gamma+1}\right)^{(\gamma+1)/2/(\gamma-1)}$
