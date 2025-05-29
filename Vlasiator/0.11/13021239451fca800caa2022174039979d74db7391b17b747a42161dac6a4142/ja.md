```
getheatfluxvector(meta, VDF; species="proton")
getheatfluxvector(meta, vcellids, vcellf; species="proton")
getheatfluxvector(vmesh::VMeshInfo, vcellids, vcellf)
```

`meta` に関連付けられた `VDF` から `species` の熱フラックスベクトル (3成分) を取得します。qᵢ = m/2 * ∫ (v - u)²(v - u)ᵢ * f(r,v) dV。あるいは、[`getdensity`](@ref) のように `vcellids`、`vcellf` を直接渡すこともできます。
