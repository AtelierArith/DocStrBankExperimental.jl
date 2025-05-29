```
uniaxial_increment!(material::AbstractMaterial, dstrain11::Real, dt::Real;
                    dstrain::AbstractVector{<:Real}=[dstrain11, -0.3*dstrain11, -0.3*dstrain11, 0.0, 0.0, 0.0],
                    max_iter::Integer=50, norm_acc::Real=1e-9)
```

Find a compatible strain increment for `material`.

The material state (`material.variables`) and the component 11 of the *strain* increment are taken as prescribed.

Convenience function; see `general_increment!`.

See `find_dstrain!`.
