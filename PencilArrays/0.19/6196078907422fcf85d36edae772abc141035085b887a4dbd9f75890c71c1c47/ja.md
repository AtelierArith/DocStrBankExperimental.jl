```
permutation(::Type{<:PencilArray})
permutation(x::PencilArray)
permutation(x::PencilArrayCollection)
```

与えられた `PencilArray` に関連するインデックスの順列を取得します。

関連する順列がない場合は `NoPermutation()` を返します。
