```
Surface
```

Struct containing all the data read from a Ticra-compatible regular x-y grid surface file.

### Fields

  * `text::String`: Descriptive string.
  * `idstrg::String`: Identification text.
  * `x::AbstractRange`: The x coordinates at which the surface is sampled.
  * `y::AbstractRange`: The y coordinates at which the surface is sampled.
  * `z::Matrix{Float64}`:  `z[i,j]` contains the surface $z$-coordinate sampled at $x$ = `x[i]` and $y$ = `y[j]`.
