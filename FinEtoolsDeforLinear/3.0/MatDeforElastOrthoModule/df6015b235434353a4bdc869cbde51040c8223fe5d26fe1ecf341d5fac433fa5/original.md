```
MatDeforElastOrtho(
    mr::Type{MR},
    E1::N,
    E2::N,
    E3::N,
    nu12::N,
    nu13::N,
    nu23::N,
    G12::N,
    G13::N,
    G23::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

Create elastic orthotropic material.

Convenience version with only the specification of the elastic properties.
