```
DeflatedNEPLinSolverCreator(orglinsolvercreator)
```

これは、デフレートされたNEPのケースのためのクリエイターです。引数`orglinsolvercreator`は、元のNEPのための`LinSolverCreator`です。拡張された線形システム

$$
[M, U; X^T, 0][v1; v2] = [b1; b2]
$$

は、元のNEPの線形ソルバーを再利用してシュール補完戦略で解かれます。したがって、事前に計算されたエンティティ（例えば、因子分解や前処理器など）を再利用できます。

NB1: 実装は最小指数 = 1を仮定しています。NB2: シュール補完は明示的に形成されます。したがって、いくつかのデフレートされた固有値に対してのみ効率的です。

参照: [`DeflatedNEPLinSolver`](@ref), [`create_linsolver`](@ref), [`deflate_eigpair`](@ref)

# 参考文献

  * C. Effenberger, Robust successive computation of eigenpairs for nonlinear eigenvalue problems. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.
