```
Amodule(A::AbstractAssociativeAlgebra, M::Vector{<:MatElem})
```

与えられた代数 $A$ と体 $K$ 上の $\dim(A)$ の正方行列のリスト $M$ に対して、`basis(A)[i]` が右から `M[i]` を介して作用する $A$-モジュールを構築します。
