```
general_increment!(material::AbstractMaterial, dstrain_knowns::AbstractVector{Union{T, Missing}},
                   dstrain::AbstractVector{Union{T, Missing}}=dstrain_knowns,
                   max_iter::Integer=50, norm_acc::T=1e-9) where T <: Real
```

Find a compatible strain increment for `material`.

The material state (`material.variables`) and any non-`missing` components of the *strain* increment `dstrain_knowns` are taken as prescribed. Any `missing` components will be solved for.

This routine computes the `missing` components of the strain increment, such that those components of the new stress state that correspond to the `missing` strain increment components, remain at the old values stored in `material.variables.stress`. (Often in practice, those old values are set to zero, allowing simulation of uniaxial push-pull tests and similar.)

"New" stress state means the stress state after integrating the material by one timestep of length `dt`.

The type of the initial guess `dstrain` is `AbstractVector{Union{T, Missing}}` only so we can make it default to `dstrain_knowns`, which has that type. Any `missing` components in the initial guess `dstrain` will be replaced by zeroes before we invoke the solver.

See `find_dstrain!`.
