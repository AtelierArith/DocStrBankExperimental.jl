```
  BoundaryValueDiffEqMIRKN.MIRKN4(; nlsolve = NewtonRaphson(), jac_alg = BVPJacobianAlgorithm(),
          defect_threshold = 0.1, max_num_subintervals = 3000)
```

4次の単調暗黙的ルンゲ・クッタ・ニーストルム法。

## キーワード引数

```
- `nlsolve`: 内部非線形ソルバー。SciMLの
  `NonlinearProblem`インターフェースに準拠する任意のソルバーを使用できます。ソルバーの自動微分引数は無視され、カスタムヤコビアンアルゴリズムが使用されます。
- `jac_alg`: 非線形ソルバーに使用されるヤコビアンアルゴリズム。デフォルトは
  `BVPJacobianAlgorithm()`で、入力タイプと問題タイプに基づいて最適なアルゴリズムを自動的に決定します。
  - `TwoPointBVProblem`の場合、`diffmode`のみが使用されます（可能であればデフォルトは
    `AutoSparse(AutoForwardDiff())`、そうでなければ`AutoSparse(AutoFiniteDiff())`）。
  - `BVProblem`の場合、`bc_diffmode`と`nonbc_diffmode`が使用されます。`nonbc_diffmode`のデフォルトは、可能であれば`AutoSparse(AutoForwardDiff())`、そうでなければ`AutoSparse(AutoFiniteDiff())`です。`bc_diffmode`のデフォルトは、可能であれば`AutoForwardDiff`、そうでなければ`AutoFiniteDiff`です。
- `defect_threshold`: 欠陥制御のための閾値。
- `max_num_subintervals`: 最大サブ区間の数、デフォルトは3000です。
```

!!! 注     型の安定性のために、`BVPJacobianAlgorithm`のForwardDiff ADTypesのチャンクサイズを提供する必要があります。

## 参考文献

```bibtex
@article{Muir2001MonoImplicitRM,
    title={Mono-Implicit Runge-Kutta-Nystr{"o}m Methods with Application to Boundary Value Ordinary Differential Equations},
    author={Paul H. Muir and Mark F. Adams},
    journal={BIT Numerical Mathematics},
    year={2001},
    volume={41},
    pages={776-799}
}
```
