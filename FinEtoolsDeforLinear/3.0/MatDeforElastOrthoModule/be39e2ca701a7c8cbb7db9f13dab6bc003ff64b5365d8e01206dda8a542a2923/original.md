```
MatDeforElastOrtho(
    mr::Type{MR},
    mass_density::N,
    E::N,
    nu::N,
    CTE::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

Create elastic orthotropic material which is really isotropic.

Convenience version with only the specification of the mass density, and the elastic and thermal expansion properties.
