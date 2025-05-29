```
is_conjugate(M::ZZMatrix, N::ZZMatrix) -> Bool, ZZMatrix
```

`M = U\cdot N\cdot U^{-1}` となる行列 $U$ が存在する場合は `true` と行列を返し、そうでない場合は `false` と $0$ を返します。$M$ の特性多項式は平方フリーである必要があります。
