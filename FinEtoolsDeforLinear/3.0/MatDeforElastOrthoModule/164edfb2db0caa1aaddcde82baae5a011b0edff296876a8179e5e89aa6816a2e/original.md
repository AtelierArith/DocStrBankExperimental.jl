```
MatDeforElastOrtho(
    mr::Type{MR},
    mass_density::N,
    E1::N,
    E2::N,
    E3::N,
    nu12::N,
    nu13::N,
    nu23::N,
    G12::N,
    G13::N,
    G23::N,
    CTE1::N,
    CTE2::N,
    CTE3::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

Create elastic orthotropic material.
