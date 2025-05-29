```
from_euler_phases(zₐ, zᵦ, zᵧ)
from_euler_phases(z)
```

Return the quaternion corresponding to these Euler phases.

Interpreting the input quaternion as a rotation (though its normalization scales out), we can define the complex Euler phases from the Euler angles (α, β, γ) as

```
zₐ ≔ exp(i*α)
zᵦ ≔ exp(i*β)
zᵧ ≔ exp(i*γ)
```

These are more useful geometric quantites than the angles themselves — being involved in computing spherical harmonics and Wigner's 𝔇 matrices — and can be computed from the components of the corresponding quaternion algebraically (without the use of transcendental functions).

# Parameters

  * `z::Vector{Complex{T}}`: complex vector of length 3, representing the complex phases (zₐ, zᵦ, zᵧ) in that order.

# Returns

  * `R::Quaternion{T}`

# See Also

  * [`to_euler_phases`](@ref): Convert quaternion to Euler phases
  * [`to_euler_angles`](@ref): Convert quaternion to Euler angles
  * [`from_euler_angles`](@ref): Create quaternion from Euler angles
