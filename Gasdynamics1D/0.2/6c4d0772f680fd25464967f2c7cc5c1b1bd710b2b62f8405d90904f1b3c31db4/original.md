```
TemperatureRatio(M1::MachNumber,NormalShock[;gas=Air])
```

Return the ratio of temperatures after and before a normal shock, given the Mach number `M1` before the shock, using the equation

$\dfrac{T_2}{T_1} = 1 + 2\dfrac{(\gamma-1)}{(\gamma+1)^2}\dfrac{(1+\gamma M_1^2)(M_1^2-1)}{M_1^2}$
