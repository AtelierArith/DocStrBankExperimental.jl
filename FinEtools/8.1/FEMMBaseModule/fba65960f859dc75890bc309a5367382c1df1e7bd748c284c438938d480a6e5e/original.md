```
integratefieldfunction(
    self::AbstractFEMM,
    geom::NodalField{GFT},
    afield::FL,
    fh::F;
    initial::R = zero(FT),
    m = -1,
) where {GFT, T, FL<:ElementalField{T}, F<:Function,R}
```

Integrate a elemental-field function over the discrete manifold.

  * `afield` = ELEMENTAL field to supply the value within the element (one value per element),
  * `fh` = function taking position and an array of field values for the element as arguments, returning value of type `R`.  The function `fh` must take two arguments, `x` which is the location, and `val` which is the value of the field at that location. The rectangular array of field values `val`  has one row, and as many columns as there are degrees of freedom per node.
  * `m` = dimension of the manifold over which to integrate; `m < 0` means that the dimension is controlled by the manifold dimension of the elements.

Integrates a  function returning a scalar value of type `R`, which is initialized by `initial`.
