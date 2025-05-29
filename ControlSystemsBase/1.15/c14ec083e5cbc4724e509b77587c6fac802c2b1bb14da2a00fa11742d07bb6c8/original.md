```
LsimWorkspace(sys::AbstractStateSpace, N::Int)
LsimWorkspace(sys::AbstractStateSpace, u::AbstractMatrix)
LsimWorkspace{T}(ny, nu, nx, N)
```

Generate a workspace object for use with the in-place function [`lsim!`](@ref). `sys` is the discrete-time system to be simulated and `N` is the number of time steps, alternatively, the input `u` can be provided instead of `N`. Note: for threaded applications, create one workspace object per thread. 
