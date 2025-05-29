```
nblocks(A[, i])
```

`Jets` ブロック演算子 `A::Union{Jet, Jop}` の範囲と定義域のブロック数を返します。`i` が指定されている場合、`i = 1` のときは `nblocks(range(jet))` を返し、それ以外の場合は `nblocks(domain(jet))` を返します。
