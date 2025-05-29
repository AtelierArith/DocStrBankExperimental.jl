```
FLStarOverD(M::MachNumber,FannoFlow[;gas=Air])
```

Compute the friction factor times distance to sonic point, divided by diameter, for the given Mach number `M`, using the equation

$\dfrac{fL^*}{D} = \dfrac{1-M^2}{\gamma M^2} + \dfrac{\gamma+1}{2\gamma} \ln \left(\dfrac{(\gamma+1)M^2}{2+(\gamma-1)M^2}\right)$
