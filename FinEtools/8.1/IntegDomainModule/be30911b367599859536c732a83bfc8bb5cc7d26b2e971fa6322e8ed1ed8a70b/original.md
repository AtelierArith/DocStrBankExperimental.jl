```
Jacobianmdim(
    self::IntegDomain{MT},
    J::Matrix{T},
    loc::Matrix{T},
    conn::CC,
    N::Matrix{T},
    m::IT,
) where {MT<:AbstractFESet1Manifold, CC, T<:Number, IT}
```

Evaluate the manifold Jacobian for an m-dimensional manifold.

For an 1-dimensional finite element,  the manifold Jacobian is for

  * m=1: `Jacobiancurve`
  * m=2: `Jacobiansurface`
  * m=3: `Jacobianvolume`
