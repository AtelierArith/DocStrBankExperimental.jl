```
struct RosenzweigMacArthur{S<:Spatialness} <: Model{Community,Biomass,S,Continuous}
```

Dynamics given by

$\frac{dR}{dt} = \lambda R \bigg(1 - \frac{R}{K}\bigg) - \frac{\alpha CR}{1 +\alpha \eta R}$

$\frac{dC}{dt} = \beta \frac{\alpha CR}{1 + \alpha \eta R} - \gamma   C$
