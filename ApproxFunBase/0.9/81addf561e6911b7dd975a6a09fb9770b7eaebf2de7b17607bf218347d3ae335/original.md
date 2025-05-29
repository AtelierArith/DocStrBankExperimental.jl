```
periodic(d::Domain,k) = [ldiffbc(d,i) - rdiffbc(d,i) for i=0:k]
```

The conditions for the `k`-th order periodic problem. See also [`ldiffbc`](@ref), [`rdiffbc`](@ref), [`ivp`](@ref) and [`bvp`](@ref)
