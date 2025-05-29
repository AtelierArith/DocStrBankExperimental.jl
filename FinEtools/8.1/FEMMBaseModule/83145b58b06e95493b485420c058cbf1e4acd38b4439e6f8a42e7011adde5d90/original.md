```
integratefieldfunction(
    self::AbstractFEMM,
    geom::NodalField{GFT},
    afield::FL,
    fh::F;
    initial::R,
    m = -1,
) where {GFT, T, FL<:NodalField{T}, F<:Function,R}
```

Integrate a nodal-field function over the discrete manifold.

  * `afield` = NODAL field to supply the values at the nodes, which are interpolated to the quadrature points,
  * `fh` = function taking position and an array of field values for the element as arguments, returning value of type `R`.  The function `fh` must take two arguments, `x` which is the location, and `val` which is the value of the field at that location. The rectangular array of field values `val`  has one row, and as many columns as there are degrees of freedom per node.
  * `m` = dimension of the manifold over which to integrate; `m < 0` means that the dimension is controlled by the manifold dimension of the elements.

Integrates a  function returning a scalar value of type `R`, which is initialized by `initial`.
