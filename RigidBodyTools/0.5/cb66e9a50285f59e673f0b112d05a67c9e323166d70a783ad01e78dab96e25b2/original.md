```
exogenous_position_vector(x::AbstractVector,ls::RigidBodyMotion,jid::Int)
```

Returns a view of the exogenous dof position(s), if any, of joint `jid` in the global state vector `x`.
