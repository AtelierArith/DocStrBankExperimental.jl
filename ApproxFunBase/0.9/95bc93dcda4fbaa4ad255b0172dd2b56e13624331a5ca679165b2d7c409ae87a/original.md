```
ivp(d::Domain, k) = [ldiffbc(d,i) for i=0:k-1]
ivp(d) = ivp(d,2)
```

The conditions for the `k`-th order initial value problem. See also [`ldiffbc`](@ref), [`bvp`](@ref) and [`periodic`](@ref).
