```
bvp(d::Domain, k) = vcat([ldiffbc(d,i) for i=0:div(k,2)-1],
                    [rdiffbc(d,i) for i=0:div(k,2)-1])
bvp(d) = bvp(d,2)
```

`k`-次境界値問題の条件。さらに[`ldiffbc`](@ref)、[`rdiffbc`](@ref)、[`ivp`](@ref)および[`periodic`](@ref)も参照してください。
