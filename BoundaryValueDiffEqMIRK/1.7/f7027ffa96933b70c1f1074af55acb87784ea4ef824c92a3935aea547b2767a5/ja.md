```
BoundaryValueDiffEqMIRK.MIRK4(; nlsolve = NewtonRaphson(), jac_alg = BVPJacobianAlgorithm(),
        defect_threshold = 0.1, max_num_subintervals = 3000)
```

4次の単調暗黙的ルンゲクッタ法。

## キーワード引数

  * `nlsolve`: 内部非線形ソルバー。SciMLの`NonlinearProblem`インターフェースに準拠した任意のソルバーを使用できます。ソルバーの自動微分引数は無視され、カスタムヤコビアンアルゴリズムが使用されます。
  * `jac_alg`: 非線形ソルバーに使用されるヤコビアンアルゴリズム。デフォルトは`BVPJacobianAlgorithm()`で、入力タイプと問題タイプに基づいて使用する最適なアルゴリズムを自動的に決定します。

      * `TwoPointBVProblem`の場合、`diffmode`のみが使用されます（可能であればデフォルトは`AutoSparse(AutoForwardDiff())`、そうでなければ`AutoSparse(AutoFiniteDiff())`）。
      * `BVProblem`の場合、`bc_diffmode`と`nonbc_diffmode`が使用されます。`nonbc_diffmode`は、可能であればデフォルトは`AutoSparse(AutoForwardDiff())`、そうでなければ`AutoSparse(AutoFiniteDiff())`です。`bc_diffmode`は、可能であればデフォルトは`AutoForwardDiff`、そうでなければ`AutoFiniteDiff`です。
  * `defect_threshold`: 欠陥制御のための閾値。
  * `max_num_subintervals`: 最大サブ区間の数、デフォルトは3000です。

!!! note
    型の安定性のために、`BVPJacobianAlgorithm`のForwardDiff ADTypesのチャンクサイズを提供する必要があります。


## 参考文献

```bibtex
@article{Enright1996RungeKuttaSW,
    title={Runge-Kutta Software with Defect Control for Boundary Value ODEs},
    author={Wayne H. Enright and Paul H. Muir},
    journal={SIAM J. Sci. Comput.},
    year={1996},
    volume={17},
    pages={479-497}
}
```
