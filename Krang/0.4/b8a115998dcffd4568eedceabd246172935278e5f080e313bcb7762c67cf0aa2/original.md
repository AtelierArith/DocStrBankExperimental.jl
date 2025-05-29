```julia
emission_coordinates(
    pix::Krang.AbstractPixel,
    τ
) -> Tuple{Any, Any, Any, Any, Any, Any, Bool}

```

Ray trace a point that appears at the screen coordinate (`α`, `β`) for an observer located at inclination θo

# Arguments

  * `pix` : Pixel information
  * `τ` : Mino Time
