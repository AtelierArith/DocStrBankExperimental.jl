```
stress_driven_general_increment!(material::AbstractMaterial,
                                 dstress_knowns::AbstractVector{<:Union{T, Missing}},
                                 dt::Real,
                                 dstrain::AbstractVector{T},
                                 max_iter::Integer=50, norm_acc::T=1e-9) where T <: Real
```

Find a compatible strain increment for `material`.

The material state (`material.variables`) and any non-`missing` components of the *stress* increment `dstress_knowns` are taken as prescribed.

This routine computes a *strain* increment such that those components of the new stress state, that correspond to non-`missing` components of `dstress_knowns`, match those components of `material.variables.stress + dstress_knowns`.

For any `missing` components of `dstress_knowns`, the new stress state will match the corresponding components of `material.variables.stress`. (So the `missing` components act as if they were zero.)

*All* strain increment components will be solved for. If you need to prescribe some of them, while also prescribing stresses, see `general_mixed_increment!`.

"New" stress state means the stress state after integrating the material by one timestep of length `dt`.

`dstrain` is the initial guess for the strain increment.

See `find_dstrain!`.
