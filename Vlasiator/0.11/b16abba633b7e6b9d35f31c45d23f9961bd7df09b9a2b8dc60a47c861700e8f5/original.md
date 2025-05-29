```
getdensity(meta, VDF; species="proton")
getdensity(meta, vcellf; species="proton")
getdensity(vmesh::VMeshInfo, vcellf)
```

Get density from `VDF` of `species` associated with `meta`, n = ∫ f(r,v) dV. Alternatively, one can directly pass `vcellids` as original indices of nonzero VDFs and `vcellf` as their corresponding values.
