```
vmatchgen(mol1::MolGraph, mol2::MolGraph) -> Function
vmatchgen(mol1::MolGraph{T1,V1,E1}, mol2::MolGraph{T2,V2,E2}
    ) where {T1,T2,V1,V2<:QueryTree,E1,E2} -> Function
vmatchgen(mol1::MolGraph{T1,V1,E1}, mol2::MolGraph{T2,V2,E2}
    ) where {T1,T2,V1<:QueryTree,V2<:QueryTree,E1,E2}
```

グラフ同型性アルゴリズムのためのデフォルトの頂点属性マッチング関数を返します。
