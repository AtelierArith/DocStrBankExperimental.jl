```
permutation(::Type{<:Pencil}) -> AbstractPermutation
permutation(p::Pencil)        -> AbstractPermutation
```

与えられたペンシル構成に関連するインデックスの置換を取得します。

関連する置換がない場合は `NoPermutation()` を返します。
