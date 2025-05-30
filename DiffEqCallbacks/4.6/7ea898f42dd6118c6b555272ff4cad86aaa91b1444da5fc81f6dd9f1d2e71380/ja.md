```
ManifoldProjection(
    manifold; nlsolve = missing, save = true, autonomous = nothing,
    manifold_jacobian = nothing, autodiff = nothing, kwargs...)
```

多くの場合、解が存在する多様体を宣言したいと思うかもしれません。数学的には、多様体 `M` は関数 `g` によって、`g(u) = 0` となる点の集合として定義されます。埋め込まれた多様体は、解を制約する低次元のオブジェクトである可能性があります。例えば、`g(u) = E(u) - C` のように、`E` は状態 `u` におけるシステムのエネルギーを表し、エネルギーが一定でなければならない（エネルギー保存）ことを意味します。したがって、多様体を定義することによって、解が存在する場所を指定することで、解の望ましい特性を保持することができます。

`ManifoldProjection` は、選択した多様体 `g` に対して微分方程式の解を投影し、特性を保持しながら順序を保ちます。これは、決定論的および確率的な場合の収束証明の結果であり、ステップ後の多様体への投影が同じ収束率を保つため、任意のアルゴリズムは特性を保持するように簡単に拡張できます。解が特定の多様体上に存在することが期待される場合や、そのような特性を保持する場合、これは収束特性を変更することなく保存法則を保証します。

## 引数

  * `manifold`: 多様体の残差関数。ODEProblem がインプレース問題である場合、`g` は `g(resid, u, p)` または `g(resid, u, p, t)` の形式のインプレース関数でなければなりません。同様に、ODEProblem がアウトオブプレース問題である場合、`g` は `g(u, p)` または `g(u, p, t)` の形式の関数でなければなりません。

## キーワード引数

  * `nlsolve`: ほとんどのケースで機能する特別な単一因子化アルゴリズム（`missing` で示される）にデフォルト設定されています（詳細は [1] を参照）。代わりに、[NonlinearSolve.jl フォーマット](https://docs.sciml.ai/NonlinearSolve/stable/basics/solve/) で定義された非線形ソルバーを指定できます。さらに、NonlinearSolve.jl がロードされていて `nothing` が指定された場合、ポリアルゴリズムが使用されます。
  * `save`: 標準の保存を行うかどうか（コールバック後に適用される）
  * `autonomous`: `g` が `g(resid, u, p)` または `g(u, p)` の形式の自律関数であるかどうか。ランタイムの分岐を無効にするために `Val(::Bool)` として指定します。`nothing` の場合、`g` のシグネチャから推測しようとします。
  * `residual_prototype`: 多様体残差のサイズ。指定されていない場合、インプレースの場合は `u` と同じであると仮定します。そうでない場合は、サイズを決定するために `manifold` の単一評価を実行します。
  * `kwargs`: `nlsolve` が `missing` でない場合、他のすべてのキーワード引数は [NonlinearSolve.jl](https://docs.sciml.ai/NonlinearSolve/stable/basics/solve/) に渡されます。
  * `autodiff`: `manifold_jacobian` が指定されていない場合にヤコビアンを計算するために使用する自動微分アルゴリズム。`manifold_jacobian` が指定されていない場合は、これを指定する必要があります。
  * `manifold_jacobian`: 多様体のヤコビアン（状態に関して）。これは `manifold` と同じシグネチャを持ち、最初の引数はインプレースの場合のヤコビアンです。

### Saveat 警告

`ManifoldProjection` コールバックは、積分区間の端点を変更し、内部補間の仮定を破ることに注意してください。このため、saveat によって与えられた値は順序が一致しません。ただし、補間誤差は投影による変化に比例する可能性があるため、投影が小さな変化をもたらす場合は安全です。しかし、各投影から大きな変化がある場合は、停止/投影時のみ保存することを検討すべきです。これを行うには、`tstops` を `saveat` と同じ値に設定します。これを行うことで、今度は積分器がすべての保存ポイントで停止することを強制されるため、パフォーマンスに影響がありますが、これは ManifoldProjection であっても積分器の順序と一致することが保証されます。

## 参考文献

[1] Ernst Hairer, Christian Lubich, Gerhard Wanner. Geometric Numerical Integration: Structure-Preserving Algorithms for Ordinary Differential Equations. Berlin ; New York :Springer, 2002. ```
