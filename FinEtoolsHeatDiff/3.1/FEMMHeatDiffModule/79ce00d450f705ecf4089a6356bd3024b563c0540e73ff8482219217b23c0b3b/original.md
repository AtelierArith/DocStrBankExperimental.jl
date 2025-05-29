```
inspectintegpoints(self::FEMMHeatDiff, geom::NodalField{GFT}, u::NodalField{T}, temp::NodalField{FT}, felist::VecOrMat{IntT}, inspector::F, idat, quantity=:heatflux; context...) where {T<:Number, GFT, FT, IntT, F<:Function}
```

Inspect integration point quantities.

# Arguments

  * `geom` - reference geometry field
  * `u` - displacement field (ignored)
  * `temp` - temperature field
  * `felist` - indexes of the finite elements that are to be inspected:   The fes to be included are: `fes[felist]`.
  * `context`    - structure: see the update!() method of the material.
  * `inspector` - function with the signature       `idat = inspector(idat, j, conn, x, out, loc);`  where   `idat` - a structure or an array that the inspector may          use to maintain some state,  for instance heat flux, `j` is the         element number, `conn` is the element connectivity, `out` is the         output of the `update!()` method,  `loc` is the location of the         integration point in the *reference* configuration.

# Output

The updated inspector data is returned.
