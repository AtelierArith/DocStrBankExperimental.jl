```
getvelocity(meta, VDF; species="proton")
getvelocity(meta, vcellids, vcellf; species="proton")
getvelocity(vmesh::VMeshInfo, vcellids, vcellf)
```

`species`の`VDF`からバルク速度を取得します。u = ∫ v * f(r,v) dV / n。あるいは、[`getdensity`](@ref)のように`vcellids`、`vcellf`を直接渡すこともできます。
