```
struct EigenEigSolver <: EigSolver
```

Juliaの組み込みのeigen()を呼び出す線形固有値問題ソルバーです。

`EigenEigSolver(A, [B,])`として構築され、次の問題を解決します。

$$
Ax = λBx
$$

パラメータ`B`はオプションで、デフォルトは単位行列であり、標準の線形固有値問題が解決されます。

関連情報: [`EigSolver`](@ref) および [`eig_solve`](@ref)
