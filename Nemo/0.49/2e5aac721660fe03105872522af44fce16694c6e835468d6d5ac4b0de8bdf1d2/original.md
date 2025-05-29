```
snf_with_transform(A::ZZMatrix, l::Bool = true, r::Bool = true) -> ZZMatrix, ZZMatrix, ZZMatrix
```

Given some integer matrix $A$, compute the Smith normal form (elementary divisor normal form) of $A$. If `l` and/ or `r` are true, then the corresponding left and/ or right transformation matrices are computed as well.
