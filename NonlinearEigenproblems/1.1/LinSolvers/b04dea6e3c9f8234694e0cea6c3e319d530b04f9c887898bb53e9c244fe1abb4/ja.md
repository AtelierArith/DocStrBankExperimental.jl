```
struct DefaultEigSolver <: EigSolver
```

スパース性をチェックし、それに応じて適切なソルバーを割り当てる線形固有値問題ソルバーです。

関連情報: [`EigSolver`](@ref), [`eig_solve`](@ref), [`EigenEigSolver`](@ref), [`ArnoldiEigSolver`](@ref)
