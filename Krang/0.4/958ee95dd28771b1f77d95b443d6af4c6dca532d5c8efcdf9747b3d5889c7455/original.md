```julia
emission_coordinates(
    pix::Krang.AbstractPixel,
    θs,
    isindir,
    n
) -> Tuple{Any, Any, Any, Any, Any, Bool}

```

Emission radius and azimuthal angle for point originating at inclination θs whose nth order image appears at the screen coordinate (`α`, `β`) for an observer located at inclination θo.

# Arguments

  * `pix` : Pixel information
  * `θs` : Emission Inclination
  * `isindir` : Whether emission to observer is direct or indirect
  * `n` : Image index
