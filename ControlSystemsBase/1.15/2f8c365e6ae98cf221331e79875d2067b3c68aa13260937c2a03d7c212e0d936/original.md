```
res = lsim!(ws::LsimWorkspace, sys::AbstractStateSpace{<:Discrete}, u, [t]; x0)
```

In-place version of [`lsim`](@ref) that takes a workspace object created by calling [`LsimWorkspace`](@ref). *Notice*, if `u` is a function, `res.u === ws.u`. If `u` is an array, `res.u === u`.
