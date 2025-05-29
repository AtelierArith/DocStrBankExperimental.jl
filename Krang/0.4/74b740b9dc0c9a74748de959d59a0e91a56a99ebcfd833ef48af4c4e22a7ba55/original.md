```julia
emission_inclination(pix::Krang.AbstractPixel, rs, νr)

```

Emission inclination for point originating at inclination rs whose nth order image appears at screen coordinate (`α`, `β`).

# Arguments

  * `pix` : Pixel information
  * `rs` : Emission radius
  * `νr` : Sign of radial velocity direction at emission. This is always positive for case 3 and case 4 geodesics.
