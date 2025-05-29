```
surface_velocity!(u::AbstractVector,v::AbstractVector,bl::BodyList,x::AbstractVector,m::RigidBodyMotion,t::Real[;axes=0,frame=axes,motion_part=:full])
```

Calculate the surface velocity components `u` and `v` for the points on bodies `bl`. The function evaluates prescribed kinematics at time `t` and extracts non-prescribed (exogenous and unconstrained) velocities from state vector `x`. There are three keyword arguments that can change the behavior of this function: `axes` determines whether the components returned are expressed in the inertial coordinate system (0, the default) or another body's coordinates (the body ID); `frame` specifies that the motion should be measured relative to another reference body's velocity (by default, 0); and `motion_part` determines whether the entire reference body velocity is used (`:full`, the default), only the angular part (`:angular`), or only the linear part (`:linear`).
