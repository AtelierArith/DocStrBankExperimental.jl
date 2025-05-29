```julia
emission_radius(
    pix::Krang.AbstractPixel,
    τ
) -> Tuple{Any, Any, Any, Bool}

```

Emission radius for point originating at at Mino time τ whose image appears at the screen coordinate (`α`, `β`).  Returns 0 if the emission coordinates do not exist for that screen coordinate.

# Arguments

-`pix` : Pixel information

  * `τ` : Mino time
