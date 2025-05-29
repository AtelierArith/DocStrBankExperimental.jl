```
MachNumber(fL_over_D::FLOverD,FannoFlow[;gas=Air]) -> MachNumber, MachNumber
```

Compute the subsonic and supersonic Mach numbers, given the ratio friction factor times distance to sonic point, divided by diameter, `fL_over_D`, by solving the equation

$\dfrac{fL^*}{D} = \dfrac{1-M^2}{\gamma M^2} + \dfrac{\gamma+1}{2\gamma} \ln \left(\dfrac{(\gamma+1)M^2}{2+(\gamma-1)M^2}\right)$
