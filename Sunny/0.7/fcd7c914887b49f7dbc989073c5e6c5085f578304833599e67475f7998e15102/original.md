```
set_field_at!(sys::System, B_μB, site::Site)
```

Sets the external magnetic field $𝐁$ scaled by the Bohr magneton $μ_B$ for a single [`Site`](@ref). This scaled field has units of energy and couples directly to the dimensionless [`magnetic_moment`](@ref). Note that a given system of [`Units`](@ref) will implicitly use the Bohr magneton to convert between field and energy dimensions.

See the documentation of [`set_field!`](@ref) for more information.
