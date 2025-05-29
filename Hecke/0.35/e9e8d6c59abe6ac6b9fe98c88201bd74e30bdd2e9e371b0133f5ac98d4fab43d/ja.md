```
Amodule(A::AbstractAssociativeAlgebra, M::Vector{<:MatElem})
```

与えられた代数 $A$ が体 $K$ 上にあり、$K$ 上の正方行列のリスト $\dim(A)$ がある場合、`basis(A)[i]` が右から `M[i]` を介して作用する $A$-モジュールを構築します。
