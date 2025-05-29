```
getpressure(meta, VDF; species="proton")
getpressure(meta, vcellids, vcellf; species="proton")
getpressure(vmesh::VMeshInfo, vcellids, vcellf)
```

Get pressure tensor (6 components: Pxx, Pyy, Pzz, Pyz, Pzx, Pxy) of `species` from `VDF` associated with `meta`, pᵢⱼ = m * ∫ (v - u)ᵢ(v - u)ⱼ * f(r,v) dV. Alternatively, one can directly pass `vcellids`, `vcellf`, as in [`getdensity`](@ref).
