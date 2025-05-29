```
body_velocities(x::AbstractVector,t::Real,ls::RigidBodyMotion) -> PluckerMotionList
```

Compute the velocities of bodies for the rigid body system `ls`, expressing each in its own coordinate system. To carry this out, the function evaluates velocities of dofs with prescribed kinematics at time `t` and and obtains the remaining free dofs (exogenous and unconstrained) from the state vector `x`.
