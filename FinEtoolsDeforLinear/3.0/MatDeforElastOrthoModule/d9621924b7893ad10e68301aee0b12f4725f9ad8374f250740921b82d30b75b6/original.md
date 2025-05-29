```
MatDeforElastOrtho(
    mr::Type{MR},
    E::N,
    nu::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

Create elastic orthotropic material which is really isotropic.

Convenience version with only the specification of the elastic properties.
