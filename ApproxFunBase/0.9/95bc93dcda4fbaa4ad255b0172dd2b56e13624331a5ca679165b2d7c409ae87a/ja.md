```
ivp(d::Domain, k) = [ldiffbc(d,i) for i=0:k-1]
ivp(d) = ivp(d,2)
```

`k`-次の初期値問題の条件。 [`ldiffbc`](@ref)、[`bvp`](@ref)、および[`periodic`](@ref)も参照してください。
