```
from_euler_angles(α, β, γ)
```

Come over from the dark side.

Assumes the Euler angles correspond to the quaternion `R` via

```
R = exp(α𝐤/2) * exp(β𝐣/2) * exp(γ𝐤/2)
```

where 𝐣 and 𝐤 rotate about the fixed $y$ and $z$ axes, respectively, so this reprents an initial rotation (in the positive sense) through an angle $γ$ about the axis $z$, followed by a rotation through $β$ about the axis $y$, and a final rotation through $α$ about the axis $z$.  This is equivalent to performing an initial rotation through $α$ about the axis $z$, followed by a rotation through $β$ about the *rotated* axis $y'$, followed by a rotation through $γ$ about the *twice-rotated* axis $z''$. The angles are naturally assumed to be in radians.

NOTE: Before opening an issue reporting something "wrong" with this function, be sure to read all of [this page](https://github.com/moble/quaternion/wiki/Euler-angles-are-horrible), *especially* the very last section about opening issues or pull requests.

# See Also

  * [`to_euler_angles`](@ref): Convert quaternion to Euler angles
  * [`to_euler_phases`](@ref): Convert quaternion to Euler phases
  * [`from_euler_phases`](@ref): Create quaternion from Euler phases
