```
motion_rhs!(dxdt::AbstractVector,x::AbstractVector,p::Tuple{RigidBodyMotion,BodyList},t::Real)
```

Sets the right-hand side vector `dxdt` (mutating) for linked system `ls` of bodies `bl`, using the current state vector `x`, the current time `t`.
