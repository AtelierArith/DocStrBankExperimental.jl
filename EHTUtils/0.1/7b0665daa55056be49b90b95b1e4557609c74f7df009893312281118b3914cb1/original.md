```
get_solidangle(x, [y=0; angunit=u"rad", angunitout=nothing, satype="pixel"])
```

compute the solid angle for a given set of the angular sizes at specified units of angular sizes in a specified type.

# Arguments

  * `Δx, Δy::Real`:   the size of the area in two orthogonal directions. if `Δy <= 0`, `Δy = Δx`.
  * `angunit::Unitful.Units or Unitful.Quantity`:   the angular unit of `Δx` and `Δy`. Default is `rad`
  * `angunitout::Unitful.Units, Unitful.Quantity or nothing`:    the angular unit for the output solid angle. If nothing is specified,   use the same unit specified in `angunit`.
  * `satype::Symbol`   The type of the output solid angle:   `:pixel` for the solid angle of the rectangular area, and   `:beam` for the beam solid angle.   For `:beam`, Δx, Δy will be interperted as Gaussian FWHMs.
