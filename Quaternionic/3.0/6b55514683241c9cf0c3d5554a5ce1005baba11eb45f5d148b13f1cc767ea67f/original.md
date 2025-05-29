```
to_euler_phases(q)
```

Convert input quaternion to complex phases of Euler angles

Interpreting the input quaternion as a rotation (though its normalization scales out), we can define the complex Euler phases from the Euler angles (α, β, γ) as

```
zₐ ≔ exp(i*α)
zᵦ ≔ exp(i*β)
zᵧ ≔ exp(i*γ)
```

These are more useful geometric quantites than the angles themselves — being involved in computing spherical harmonics and Wigner's 𝔇 matrices — and can be computed from the components of the corresponding quaternion algebraically (without the use of transcendental functions).

Note that `to_euler_phases!(z, q)` is supported for backwards compatibility, but because this function returns an `SVector`, there is probably no advantage to the in-place approach.

# Returns

  * `z::SVector{Complex{T}}`: complex phases (zₐ, zᵦ, zᵧ) in that order.

# See Also

  * [`from_euler_phases`](@ref): Create quaternion from Euler phases
  * [`to_euler_angles`](@ref): Convert quaternion to Euler angles
  * [`from_euler_angles`](@ref): Create quaternion from Euler angles
