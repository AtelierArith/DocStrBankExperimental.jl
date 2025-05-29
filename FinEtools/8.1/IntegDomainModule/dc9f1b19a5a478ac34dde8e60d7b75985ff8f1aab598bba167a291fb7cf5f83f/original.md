```
Jacobianmdim(
    self::IntegDomain{MT},
    J::Matrix{T},
    loc::Matrix{T},
    conn::CC,
    N::Matrix{T},
    m::IT,
) where {MT<:AbstractFESet3Manifold, CC, T<:Number, IT}
```

Evaluate the manifold Jacobian for an m-dimensional manifold.

For an 3-dimensional cell,  the manifold Jacobian is

  * m=3: `Jacobianvolume`
