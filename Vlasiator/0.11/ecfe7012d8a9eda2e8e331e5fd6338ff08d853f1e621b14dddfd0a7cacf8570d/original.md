```
getvelocity(meta, VDF; species="proton")
getvelocity(meta, vcellids, vcellf; species="proton")
getvelocity(vmesh::VMeshInfo, vcellids, vcellf)
```

Get bulk velocity from `VDF` of `species`, u = ∫ v * f(r,v) dV / n. Alternatively, one can directly pass `vcellids`, `vcellf`, as in [`getdensity`](@ref).
