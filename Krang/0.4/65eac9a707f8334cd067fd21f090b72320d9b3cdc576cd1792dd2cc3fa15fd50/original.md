```julia
Ir(pix::Krang.AbstractPixel, νr::Bool, rs) -> Any

```

Returns the antiderivative $I_r=\int\frac{dr}{\sqrt{\mathcal{R(r)}}}$. See [`r_potential(x)`](@ref) for an implementation of $\mathcal{R}(r)$.

# Arguments

  * `pix`  : Pixel information
  * `νr` : Sign of radial velocity direction at emission. This is always positive for case 3 and case 4 geodesics.
  * `rs` : Emission radius
