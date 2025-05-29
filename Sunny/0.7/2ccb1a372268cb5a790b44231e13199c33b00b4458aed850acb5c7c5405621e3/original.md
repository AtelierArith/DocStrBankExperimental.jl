```
set_onsite_coupling_at!(sys::System, op, site::Site)
```

Sets the single-ion anisotropy operator `op` for a single [`Site`](@ref), ignoring crystal symmetry.  The system must support inhomogeneous interactions via [`to_inhomogeneous`](@ref).

See also [`set_onsite_coupling!`](@ref).
