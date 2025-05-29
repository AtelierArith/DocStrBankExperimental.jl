```
absolute_representation_matrix(a::RelSimpleNumFieldElem) -> MatrixElem
```

`a`の絶対表現行列を返します。これは、`a`の親の$\mathbb{Q}$-基底に関して`a`との乗算を表す行列です（[`absolute_basis(::RelSimpleNumField)`](@ref)を参照）。
