```
norm_group(f::Nemo.PolyRingElem, mR::Hecke.MapRayClassGrp, is_abelian::Bool = true; of_closure::Bool = false) -> Hecke.FinGenGrpAb, Hecke.FinGenGrpAbMap

norm_group(f::Array{PolyRingElem{AbsSimpleNumFieldElem}}, mR::Hecke.MapRayClassGrp, is_abelian::Bool = true; of_closure::Bool = false) -> Hecke.FinGenGrpAb, Hecke.FinGenGrpAbMap
```

多項式 $f$ の根によって生成される拡張のノルムによって与えられるレイ類群 $R$ の部分群を計算します。`is_abelian` が true に設定されている場合、コードは体がアーベルであると仮定し、ノルム群による商が正しい順序を持つときにアルゴリズムは停止します。アルゴリズムは本質的に確率的ですが、この場合、結果は保証されます。`of_closure` が指定されている場合、分解体のノルム群が計算されます。渡されたレイ類群が十分に大きいことを確認するのは呼び出し元の責任です。
