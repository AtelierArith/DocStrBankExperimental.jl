```
MatDeforElastIso(
    mr::Type{MR},
    mass_density::N,
    E::N,
    nu::N,
    CTE::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

Create an isotropic elastic material providing all material parameters.

## Arguments

  * `mr::Type{MR}`: The type of the deformation model.
  * `mass_density::N`: The mass density of the material.
  * `E::N`: The Young's modulus of the material.
  * `nu::N`: The Poisson's ratio of the material.
  * `CTE::N`: The coefficient of thermal expansion of the material.
