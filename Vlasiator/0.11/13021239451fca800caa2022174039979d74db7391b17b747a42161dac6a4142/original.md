```
getheatfluxvector(meta, VDF; species="proton")
getheatfluxvector(meta, vcellids, vcellf; species="proton")
getheatfluxvector(vmesh::VMeshInfo, vcellids, vcellf)
```

Get heat flux vector (3 components) of `species` from `VDF` associated with `meta`, qᵢ = m/2 * ∫ (v - u)²(v - u)ᵢ * f(r,v) dV. Alternatively, one can directly pass `vcellids`, `vcellf`, as in [`getdensity`](@ref).
