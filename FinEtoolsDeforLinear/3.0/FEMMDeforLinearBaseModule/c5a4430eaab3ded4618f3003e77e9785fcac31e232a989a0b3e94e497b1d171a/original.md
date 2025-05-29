```
inspectintegpoints(
    self::FEMM,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
    felist::AbstractVector{IT},
    inspector::F,
    idat,
    quantity = :Cauchy;
    context...,
) where {
    FEMM<:AbstractFEMMDeforLinear,
    GFT<:Number,
    UFT<:Number,
    TFT<:Number,
    IT<:Integer,
    F<:Function,
}
```

Inspect integration point quantities.

# Arguments

  * `geom` - reference geometry field
  * `u` - displacement field
  * `dT` - temperature difference field
  * `felist` - indexes of the finite elements that are to be inspected: The fes to be included are: `fes[felist]`.
  * `context`    - structure: see the update!() method of the material.
  * `inspector` - functionwith the signature idat = inspector(idat, j, conn, x, out, loc); where `idat` - a structure or an array that the inspector may use to maintain some state,  for instance minimum or maximum of stress, `j` is the element number, `conn` is the element connectivity, `out` is the output of the update!() method,  `loc` is the location of the integration point in the *reference* configuration.

# Return

The updated inspector data is returned.
