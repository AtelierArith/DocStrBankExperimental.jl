```
  BoundaryValueDiffEqFIRK.LobattoIIIc4(; nlsolve = NewtonRaphson(), jac_alg = BVPJacobianAlgorithm(), nested_nlsolve = false, nest_tol = 0.0,
          defect_threshold = 0.1, max_num_subintervals = 3000)
```

4次のステージのLobattoIIIc法。

## キーワード引数

  * `nlsolve`: 内部非線形ソルバー。SciMLの`NonlinearProblem`インターフェースに準拠する任意のソルバーを使用できます。ソルバーの自動微分引数は無視され、カスタムヤコビアンアルゴリズムが使用されます。
  * `jac_alg`: 非線形ソルバーに使用されるヤコビアンアルゴリズム。デフォルトは`BVPJacobianAlgorithm()`で、入力タイプと問題タイプに基づいて最適なアルゴリズムを自動的に決定します。

      * `TwoPointBVProblem`の場合、`diffmode`のみが使用されます（可能であれば`AutoSparse(AutoForwardDiff)`がデフォルト、そうでなければ`AutoSparse(AutoFiniteDiff)`）。
      * `BVProblem`の場合、`bc_diffmode`と`nonbc_diffmode`が使用されます。`nonbc_diffmode`は、可能であれば`AutoSparse(AutoForwardDiff)`がデフォルト、そうでなければ`AutoSparse(AutoFiniteDiff)`です。`bc_diffmode`は、可能であれば`AutoForwardDiff`がデフォルト、そうでなければ`AutoFiniteDiff`です。
  * `nested_nlsolve`: 暗黙のFIRKステップのためにネストされた非線形解法を使用するかどうか。デフォルトは`true`です。`false`に設定すると、FIRKステージはグローバル残差の一部として解かれます。一般的な推奨は、大きな問題には`true`を、小さな問題には`false`を選択することです。
  * `nest_tol`: ネストされたソルバーの許容誤差。デフォルトは何も指定されておらず、`NonlinearSolve`が自動的に許容誤差を選択します。
  * `defect_threshold`: 欠陥制御のための閾値。
  * `max_num_subintervals`: 最大サブ区間の数、デフォルトは3000です。

!!! note
    型の安定性のために、`BVPJacobianAlgorithm`のForwardDiff ADTypesのチャンクサイズを提供する必要があります。


## 参考文献

LobattoおよびRadau法の参考文献：

```bibtex
@Inbook{Jay2015,
    author="Jay, Laurent O.",
    editor="Engquist, Bj{"o}rn",
    title="Lobatto Methods",
    booktitle = {Encyclopedia of {Applied} and {Computational} {Mathematics}},
    year="2015",
    publisher="Springer Berlin Heidelberg",
}
@incollection{engquist_radau_2015,
    author = {Hairer, Ernst and Wanner, Gerhard},
    title = {Radau {Methods}},
    booktitle = {Encyclopedia of {Applied} and {Computational} {Mathematics}},
    publisher = {Springer Berlin Heidelberg},
    editor="Engquist, Bj{"o}rn",
    year = {2015},
}
```

MATLABの`bvp5c`ソルバーに基づく欠陥制御の実装に関する参考文献：

```bibtex
@article{shampine_solving_nodate,
title = {Solving {Boundary} {Value} {Problems} for {Ordinary} {Diﬀerential} {Equations} in {Matlab} with bvp4c
author = {Shampine, Lawrence F and Kierzenka, Jacek and Reichelt, Mark W},
year = {2000},
}

@article{kierzenka_bvp_2008,
    title = {A {BVP} {Solver} that {Controls} {Residual} and {Error}},
    author = {Kierzenka, J and Shampine, L F},
    year = {2008},
}

@article{russell_adaptive_1978,
    title = {Adaptive {Mesh} {Selection} {Strategies} for {Solving} {Boundary} {Value} {Problems}},
    journal = {SIAM Journal on Numerical Analysis},
    author = {Russell, R. D. and Christiansen, J.},
    year = {1978},
    file = {Russell and Christiansen - 1978 - Adaptive Mesh Selection Strategies for Solving Bou.pdf:/Users/AXLRSN/Zotero/storage/HKU27A4T/Russell and Christiansen - 1978 - Adaptive Mesh Selection Strategies for Solving Bou.pdf:application/pdf},
}
```
