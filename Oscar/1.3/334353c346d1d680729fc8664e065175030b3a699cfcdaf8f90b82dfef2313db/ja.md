```
is_hermitian(B::MatElem{T}) where T <: FinFieldElem
```

行列 `B` がエルミートであるかどうかを返します。すなわち、`B = conjugate_transpose(B)` です。`B` が正方行列でない場合、または体の次数が偶数でない場合は `false` を返します。
