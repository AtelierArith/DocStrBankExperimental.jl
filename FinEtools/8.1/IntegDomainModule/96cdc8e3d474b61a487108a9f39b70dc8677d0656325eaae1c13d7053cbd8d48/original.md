```
Jacobianmdim(
    self::IntegDomain{MT},
    J::Matrix{T},
    loc::Matrix{T},
    conn::CC,
    N::Matrix{T},
    m::IT,
) where {MT<:AbstractFESet0Manifold, CC, T<:Number, IT}
```

Evaluate the manifold Jacobian for an m-dimensional manifold.

For an 0-dimensional finite element,  the manifold Jacobian is for

  * m=0: +1
  * m=1: `Jacobiancurve`
  * m=2: `Jacobiansurface`
  * m=3: `Jacobianvolume`
