```
Jacobianvolume(
    self::IntegDomain{MT},
    J::Matrix{T},
    loc::Matrix{T},
    conn::CC,
    N::Matrix{T},
) where {MT<:AbstractFESet1Manifold, CC, T<:Number}
```

Evaluate the volume Jacobian.

For the one-dimensional cell,  the volume Jacobian is (i) the product of the curve Jacobian and the other dimension (units of length squared); or,  when used as axially symmetric (ii) the product of the curve Jacobian and the circumference of the circle through the point `loc` and the other dimension (units of length).

  * `J` = Jacobian matrix
  * `loc` = location of the quadrature point in physical coordinates,
  * `conn` = connectivity of the element,
  * `N` = matrix of basis function values at the quadrature point.
