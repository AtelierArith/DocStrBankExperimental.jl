```
ematchgen(mol1::MolGraph, mol2::MolGraph) -> Function
ematchgen(mol::MolGraph{T1,V1,E1}, qmol::MolGraph{T2,V2,E2}
    ) where {T1,T2,V1,V2,E1,E2<:QueryTree}
ematchgen(mol1::MolGraph{T1,V1,E1}, mol2::MolGraph{T2,V2,E2}
    ) where {T1,T2,V1,V2,E1<:QueryTree,E2<:QueryTree}
```

グラフ同型性アルゴリズムのためのデフォルトのエッジ属性マッチング関数を返します。
