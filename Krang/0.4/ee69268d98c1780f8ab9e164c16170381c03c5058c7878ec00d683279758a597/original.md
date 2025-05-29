```julia
emission_radius(
    pix::Krang.AbstractPixel,
    θs,
    isindir,
    n
) -> Tuple{Any, Any, Any, Any, Bool}

```

Emission radius for point originating at inclination θs whose nth order image appears at the screen coordinate (`α`, `β`).  Returns 0 if the emission coordinates do not exist for that screen coordinate.

# Arguments

  * `pix` : Pixel information
  * `θs` : Emission inclination
  * `isindir` : Is emission to observer direct or indirect
  * `n` : Image index
