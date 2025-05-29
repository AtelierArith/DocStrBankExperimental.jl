```
struct DeflatedNEPLinSolver <: LinSolver
```

`DeflatedNEPLinSolver`は、膨張されたNEPに関連する線形システムを解決します。拡張された線形システムは、元のNEPの線形ソルバーを再利用してシュール補完戦略で解決されます。次のように表されます。

$$
[M, U; X^T, 0][v1; v2] = [b1; b2]
$$

NB1: 実装は最小指数 = 1を仮定しています。NB2: シュール補完は明示的に形成されます。したがって、いくつかの膨張された固有値に対してのみ効率的です。参照: [`LinSolver`](@ref), [`DeflatedNEPLinSolverCreator`](@ref), [`deflate_eigpair`](@ref)

# 参考文献

  * C. Effenberger, 非線形固有値問題のための堅牢な逐次固有対計算. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.
