```
struct RosenzweigMacArthur{S<:Spatialness} <: Model{Community,Biomass,S,Continuous}
```

動力学は次のように与えられます。

$$
\frac{dR}{dt} = \lambda R \bigg(1 - \frac{R}{K}\bigg) - \frac{\alpha CR}{1 +\alpha \eta R}
$$

$$
\frac{dC}{dt} = \beta \frac{\alpha CR}{1 + \alpha \eta R} - \gamma   C
$$
