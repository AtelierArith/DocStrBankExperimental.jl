```
reversecholesky(A, NoPivot(); check = true) -> ReverseCholesky
```

密な対称正定値行列 `A` の逆コレスキー分解を計算し、[`ReverseCholesky`](@ref) 分解を返します。行列 `A` は、[`Symmetric`](@ref) または [`Hermitian`](@ref) [`AbstractMatrix`](@ref) であるか、*完全に* 対称またはエルミートな `AbstractMatrix` であることができます。

三角形の逆コレスキー因子は、分解 `F` から `F.L` と `F.U` を介して取得でき、`A ≈ F.U * F.U' ≈ F.L' * F.L` となります。
