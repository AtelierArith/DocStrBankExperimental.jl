```
StagnationPressureRatio(M1::MachNumber,NormalShock[;gas=Air])
```

Return the ratio of stagnation pressures after and before a normal shock, given the Mach number `M1` before the shock, using the equation

$\dfrac{p_{02}}{p_{01}} = \left(\dfrac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}\right)^{\gamma/(\gamma-1)} \left(\dfrac{\gamma+1}{2\gamma M_1^2 - (\gamma-1)}\right)^{1/(\gamma-1)}$
