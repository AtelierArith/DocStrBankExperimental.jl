```
blockcheckbounds(A, inds...)
```

指定されたブロックインデックスが与えられたブロック配列の範囲内でない場合、`BlockBoundsError`をスローします。`AbstractBlockArray`のサブタイプは、カスタムブロック境界チェックの動作を提供する必要がある場合、このメソッドを特化すべきです。

```jldoctest
julia> A = BlockArray(rand(2,3), [1,1], [2,1]);

julia> blockcheckbounds(A, 3, 2)
ERROR: BlockBoundsError: attempt to access 2×2-blocked 2×3 BlockMatrix{Float64} at block index [3,2]
[...]
```
