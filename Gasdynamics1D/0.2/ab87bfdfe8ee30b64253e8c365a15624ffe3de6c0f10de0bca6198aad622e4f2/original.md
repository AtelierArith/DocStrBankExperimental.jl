```
AOverAStar(M::MachNumber,Isentropic[;gas=Air]) -> AreaRatio
```

Compute the ratio of local area to the sonic area for the given Mach number `M`, using

$\dfrac{A}{A^*} = \dfrac{1}{M} \left( \dfrac{2}{\gamma+1} \left( 1 + \dfrac{\gamma-1}{2}M^2\right)\right)^{(\gamma+1)/2/(\gamma-1)}$

Can omit the `Isentropic` argument.
