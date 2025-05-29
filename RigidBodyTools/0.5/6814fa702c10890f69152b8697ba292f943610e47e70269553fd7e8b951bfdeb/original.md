```
maxvelocity(b::Union{Body,BodyList},x::AbstractVector,m::RigidBodyMotion[,tmax=10,dt=0.05])
```

Search through the given motion state vector `x` and motion `m` applied to body `b` and return `(umax,i,t,bid)`, the maximum velocity magnitude, the global index of the body point where it occurs, the time at which it occurs, and the body on which it occurs.
