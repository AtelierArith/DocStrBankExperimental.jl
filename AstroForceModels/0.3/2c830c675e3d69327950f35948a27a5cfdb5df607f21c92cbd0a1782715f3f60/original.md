```
third_body_accel(u::AbstractArray, μ_body::Number, body_pos::AbstractArray, h::Number) -> SVector{3}{Number}
```

Compute the Acceleration from a 3rd Body Represented as a Point Mass

Since the central body is also being acted upon by the third body, the acceleration of body 𝐁 acting on  spacecraft 𝐀 in the orbiting body's 𝐂 is part of the force not acting on the central body

```
            a = ∇UB(rA) - ∇UB(rC)
```

# Arguments

  * `u::AbstractArray`: The current state of the spacecraft in the central body's inertial frame.
  * `μ_body`: Gravitation Parameter of the 3rd body.
  * `body_pos::AbstractArray`: The current position of the 3rd body in the central body's inertial frame.

# Returns

  * `SVector{3}{Number}`: Inertial acceleration from the 3rd body
