```
coinvariant_lattice(L::ZZLat, G::Vector{MatElem};
                    ambient_representation::Bool = true) -> ZZLat
coinvariant_lattice(L::ZZLat, G::MatElem;
                    ambient_representation::Bool = true) -> ZZLat
```

与えられた $\mathbf{Z}$-格子 $L$ と $L$ の自己準同型を誘導する行列のリスト $G$（または単一の行列 $G$）に対して、固定格子 $L^G$ の $L$ における直交補空間 $L_G$ を返します（[`invariant_lattice`](@ref）を参照）。

`ambient_representation` が `true`（デフォルト）である場合、自己準同型は $L$ の周囲空間に関して表現されます。そうでない場合、自己準同型は $L$ の基底に関して表現されます。
