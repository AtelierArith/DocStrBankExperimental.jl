```
MachNumber(p_over_p0::PressureRatio,Isentropic[;gas=Air])
```

Compute the Mach number corresponding to the ratio of pressure to stagnation pressure `p_over_p0`, using

$M = \left( \dfrac{2}{\gamma-1}\left(\dfrac{1}{(p/p_0)^{(\gamma-1)/\gamma}} - 1 \right)\right)^{1/2}$

Can also supply the arguments for `p` and `p0` separately, `MachNumber(p,p0)`
