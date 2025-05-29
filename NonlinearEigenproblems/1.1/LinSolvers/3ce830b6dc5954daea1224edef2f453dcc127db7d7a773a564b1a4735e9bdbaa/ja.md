```
struct ArnoldiEigSolver <: EigSolver
```

大規模かつ疎な問題のための線形固有値問題ソルバーで、JuliaパッケージArnoldiMethod.jlに実装されたArnoldi法を呼び出します。

`ArnoldiEigSolver(A, [B,])`として構築され、次の問題を解決します。

$$
Ax = λBx
$$

パラメータ`B`はオプションで、デフォルトは単位行列であり、標準的な線形固有値問題が解かれます。

関連情報: [`EigSolver`](@ref) および [`eig_solve`](@ref)
