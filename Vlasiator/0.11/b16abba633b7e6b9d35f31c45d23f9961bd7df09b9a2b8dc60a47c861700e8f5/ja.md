```
getdensity(meta, VDF; species="proton")
getdensity(meta, vcellf; species="proton")
getdensity(vmesh::VMeshInfo, vcellf)
```

`meta` に関連付けられた `species` の `VDF` から密度を取得します。n = ∫ f(r,v) dV。あるいは、非ゼロ VDF の元のインデックスとして `vcellids` を直接渡し、それに対応する値として `vcellf` を渡すこともできます。
