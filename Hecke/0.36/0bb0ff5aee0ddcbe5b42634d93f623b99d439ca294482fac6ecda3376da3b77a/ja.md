```
local_basis_matrix(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}; type = :any) -> MatElem
```

素イデアル `p` と格子 `L` が与えられたとき、$M_{p} = L_{p}$ となる格子 `M` の基底行列を返します。`p` が `L` の基底環の中のイデアルである場合、完備化は `p` の最小値で行われます（これは `p` の順序の基底環の中のイデアルです）。

  * `type == :submodule` の場合、格子 `M` は `L` の部分格子になります。
  * `type == :supermodule` の場合、格子 `M` は `L` の超格子になります。
  * `type == :any` の場合、`M` と `L` の間に包含関係がないかもしれません。
