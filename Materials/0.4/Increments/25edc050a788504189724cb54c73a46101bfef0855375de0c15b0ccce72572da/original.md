```
stress_driven_uniaxial_increment!(material::AbstractMaterial, dstress11::Real, dt::Real;
                                  dstrain::AbstractVector{<:Real}=[dstress11/200e3, -0.3*dstress11/200e3, -0.3*dstress11/200e3, 0.0, 0.0, 0.0],
                                  max_iter::Integer=50, norm_acc::Real=1e-9)
```

Find a compatible strain increment for `material`.

The material state (`material.variables`) and the component 11 of the *stress* increment are taken as prescribed.

Convenience function; see `stress_driven_general_increment!`.

See `find_dstrain!`.
