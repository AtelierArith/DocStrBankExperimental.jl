```
MachNumber(A_over_Astar::AreaRatio,Isentropic[;gas=Air]) -> MachNumber, MachNumber
```

Compute the subsonic and supersonic Mach numbers for the given ratio of area to sonic area `A_over_Astar` by solving the equation

$\dfrac{A}{A^*} = \dfrac{1}{M} \left( \dfrac{2}{\gamma+1} \left( 1 + \dfrac{\gamma-1}{2}M^2\right)\right)^{(\gamma+1)/2/(\gamma-1)}$

Can omit the `Isentropic` argument.
