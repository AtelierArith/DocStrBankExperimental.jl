```
invariant_lattice(L::ZZLat, G::Vector{MatElem};
                  ambient_representation::Bool = true) -> ZZLat
invariant_lattice(L::ZZLat, G::MatElem;
                  ambient_representation::Bool = true) -> ZZLat
```

与えられた $\mathbf{Z}$-格子 $L$ と $L$ の自己準同型を誘導する行列のリスト $G$（または単一の行列 $G$）に対して、$G$ によって固定された要素からなる格子 $L^G$ を返します。

`ambient_representation` が `true` の場合（デフォルト）、自己準同型は $L$ の周囲空間に関して表現されます。そうでない場合、自己準同型は $L$ の基底に関して表現されます。
