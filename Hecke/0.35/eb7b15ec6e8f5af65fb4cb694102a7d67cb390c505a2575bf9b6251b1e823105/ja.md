```
norm_group(f::Nemo.PolyRingElem, mR::Hecke.MapRayClassGrp, is_abelian::Bool = true; of_closure::Bool = false) -> Hecke.FinGenGrpAb, Hecke.FinGenGrpAbMap

norm_group(f::Array{PolyRingElem{AbsSimpleNumFieldElem}}, mR::Hecke.MapRayClassGrp, is_abelian::Bool = true; of_closure::Bool = false) -> Hecke.FinGenGrpAb, Hecke.FinGenGrpAbMap
```

$$
R
$$

によって与えられるレイ類群の部分群を計算します。これは、$f$の根によって生成される拡張のノルムです。`is_abelian`がtrueに設定されている場合、コードは体がアーベルであると仮定し、ノルム群による商が正しい順序を持つときにアルゴリズムは停止します。アルゴリズムは本質的に確率的ですが、この場合、結果は保証されます。`of_closure`が指定されている場合、ポリノミアルの分裂体のノルム群が計算されます。渡されるレイ類群が十分に大きいことを確認するのは呼び出し元の責任です。
