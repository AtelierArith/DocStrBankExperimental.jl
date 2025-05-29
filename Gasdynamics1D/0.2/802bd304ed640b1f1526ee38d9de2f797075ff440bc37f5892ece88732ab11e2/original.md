```
TemperatureRatio(pr::PressureRatio,Isentropic[;gas=Air])
```

Compute the ratio of temperatures between two points connected isentropically, given the ratio of pressures `pr` between those two points, using the isentropic relation

$\dfrac{T_2}{T_1} = \left(\dfrac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}$
