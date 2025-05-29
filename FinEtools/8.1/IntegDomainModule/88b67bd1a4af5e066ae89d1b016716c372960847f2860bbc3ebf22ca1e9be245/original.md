```
Jacobianvolume(
    self::IntegDomain{MT},
    J::Matrix{T},
    loc::Matrix{T},
    conn::CC,
    N::Matrix{T},
) where {MT<:AbstractFESet0Manifold, CC, T<:Number}
```

Evaluate the volume Jacobian.

For the zero-dimensional cell, the volume Jacobian is (i) the product of the point Jacobian and the other dimension (units of length cubed); or,  when used as axially symmetric (ii) the product of the point Jacobian and the circumference of the circle through the point `loc` and the other dimension (units of length squared).

  * `J` = Jacobian matrix
  * `loc` = location of the quadrature point in physical coordinates,
  * `conn` = connectivity of the element,
  * `N` = matrix of basis function values at the quadrature point.
