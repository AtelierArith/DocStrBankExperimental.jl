```
commutes(A :: Matrix, B :: Matrix; atol=ATOL :: Float64) :: Bool
```

行列 `A` が行列 `B` と可換である場合に true を返します。2 つの行列が可換であるとは、`A*B == B*A` であることを意味します。行列は互換性のある次元を持っている必要があります：

  * A: 行列、mxn 次元
  * B: 行列、nxm 次元

行列が互換性がない場合は `DomainError` がスローされます。
