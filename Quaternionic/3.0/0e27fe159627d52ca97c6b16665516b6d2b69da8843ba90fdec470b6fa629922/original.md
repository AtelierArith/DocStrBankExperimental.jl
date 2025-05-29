```
to_euler_angles(R)
```

Open Pandora's Box.

If somebody is trying to make you use Euler angles, tell them no, and walk away, and go and tell your mum.

You don't want to use Euler angles.  They are awful.  Stay away.  It's one thing to convert from Euler angles to quaternions; at least you're moving in the right direction.  But to go the other way?!  It's just not right.

Assumes the Euler angles correspond to the quaternion `R` via

```
R = exp(α𝐤/2) * exp(β𝐣/2) * exp(γ𝐤/2)
```

where 𝐣 and 𝐤 rotate about the fixed $y$ and $z$ axes, respectively, so this reprents an initial rotation (in the positive sense) through an angle $γ$ about the axis $z$, followed by a rotation through $β$ about the axis $y$, and a final rotation through $α$ about the axis $z$.  This is equivalent to performing an initial rotation through $α$ about the axis $z$, followed by a rotation through $β$ about the *rotated* axis $y'$, followed by a rotation through $γ$ about the *twice-rotated* axis $z''$. The angles are naturally assumed to be in radians.

NOTE: Before opening an issue reporting something "wrong" with this function, be sure to read all of [this page](https://github.com/moble/quaternion/wiki/Euler-angles-are-horrible), *especially* the very last section about opening issues or pull requests.

# Returns

  * `αβγ::Vector{T}`

# Raises

  * `AllHell` if you try to actually use Euler angles, when you could have been using quaternions like a sensible person.

# See Also

  * [`from_euler_angles`](@ref): Create quaternion from Euler angles
  * [`to_euler_phases`](@ref): Convert quaternion to Euler phases
  * [`from_euler_phases`](@ref): Create quaternion from Euler phases
