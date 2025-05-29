```
Jacobiansurface(
    self::IntegDomain{MT},
    J::Matrix{T},
    loc::Matrix{T},
    conn::CC,
    N::Matrix{T},
) where {MT<:AbstractFESet0Manifold, CC, T<:Number}
```

Evaluate the surface Jacobian.

For the zero-dimensional cell, the surface Jacobian is (i) the product of the point Jacobian and the other dimension (units of length squared); or,  when used as axially symmetric (ii) the product of the point Jacobian and the circumference of the circle through the point `loc` times the other dimension (units of length).

  * `J` = Jacobian matrix
  * `loc` = location of the quadrature point in physical coordinates,
  * `conn` = connectivity of the element,
  * `N` = matrix of basis function values at the quadrature point.
