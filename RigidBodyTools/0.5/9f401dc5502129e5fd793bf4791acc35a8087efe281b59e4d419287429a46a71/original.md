```
velocity_vector(x::AbstractVector,ls::RigidBodyMotion,jid::Int)
```

Returns a view of the global state vector for a linked system containing only the velocity of joint `jid`.
