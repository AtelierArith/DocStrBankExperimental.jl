```
bvp(d::Domain, k) = vcat([ldiffbc(d,i) for i=0:div(k,2)-1],
                    [rdiffbc(d,i) for i=0:div(k,2)-1])
bvp(d) = bvp(d,2)
```

The conditions for the `k`-th order boundary value problem. See also [`ldiffbc`](@ref), [`rdiffbc`](@ref), [`ivp`](@ref) and [`periodic`](@ref).
