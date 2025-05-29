```
deredd(Eby, by, m1, c1, ub) -> by0, m0, c0, ub0
```

### Purpose

Deredden stellar Stromgren parameters given for a value of E(b-y)

### Arguments

  * `Eby`: color index E(b-y), scalar (E(b-y) = 0.73*E(B-V))
  * `by`: b-y color (observed)
  * `m1`: Stromgren line blanketing parameter (observed)
  * `c1`: Stromgren Balmer discontinuity parameter (observed)
  * `ub`: u-b color (observed)

All arguments can be either scalars or arrays all of the same length.

### Output

The 4-tuple `(by0, m0, c0, ub0)`.

  * `by0`: b-y color (dereddened)
  * `m0`: line blanketing index (dereddened)
  * `c0`: Balmer discontinuity parameter (dereddened)
  * `ub0`: u-b color (dereddened)

These are scalars or arrays of the same length as the input arguments.

### Example

```jldoctest
julia> using AstroLib

julia> deredd(0.5, 0.2, 1.0, 1.0, 0.1)
(-0.3, 1.165, 0.905, -0.665)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
