```
AStar(A::Area,M::MachNumber,Isentropic[;gas=Air]) -> Area
```

Compute the sonic area for the given area `A` and Mach number `M`, using

$A^* = A M \left( \dfrac{2}{\gamma+1} \left( 1 + \dfrac{\gamma-1}{2}M^2\right)\right)^{-(\gamma+1)/2/(\gamma-1)}$

Can omit the `Isentropic` argument.
