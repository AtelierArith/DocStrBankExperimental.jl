```
periodic(d::Domain,k) = [ldiffbc(d,i) - rdiffbc(d,i) for i=0:k]
```

`k`-次の周期的問題の条件。[`ldiffbc`](@ref)、[`rdiffbc`](@ref)、[`ivp`](@ref)、および[`bvp`](@ref)も参照してください。
