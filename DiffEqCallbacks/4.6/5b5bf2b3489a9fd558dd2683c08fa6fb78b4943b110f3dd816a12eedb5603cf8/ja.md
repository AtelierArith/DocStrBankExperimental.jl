```
GeneralDomain(
    g, u = nothing; save = true, abstol = nothing, scalefactor = nothing,
    autonomous = nothing, domain_jacobian = nothing,
    nlsolve_kwargs = (; abstol = 10 * eps()), kwargs...)
```

`GeneralDomain` コールバックは、DiffEqCallbacks.jl において `PositiveDomain` コールバックの概念を任意のドメインに一般化します。

ドメインは以下によって指定されます。

  * インプレース関数 `g(resid, u, p)` または `g(resid, u, p, t)` （対応する ODEProblem がインプレース問題の場合）、または
  * アウトオブプレース関数 `g(u, p)` または `g(u, p, t)` （対応する ODEProblem がアウトオブプレース問題の場合）。

この関数は、状態ベクトル `u` の残差を時間 `t` においてそのドメインに対して計算し、`p` は対応する積分器のパラメータです。

`PositiveDomain` と同様に、次の時間ステップでの外挿値の残差が特定の許容範囲内であればステップが受け入れられます。さらに、このコールバックは、計算されたすべての状態ベクトルを希望するドメインに近く保つ `ManifoldProjection` と自動的に結合されますが、`PositiveDomain` コールバックとは対照的に、`ManifoldProjection` の非線形ソルバーは解のすべての状態ベクトルが実際にドメイン内にあることを保証できません。したがって、一般的には `PositiveDomain` コールバックが好まれるべきです。

## 引数

  * `g`: 上記のように、ドメインの暗黙的定義としての関数で、値がドメイン内にあるときにゼロになります。
  * `u`: 積分器の状態ベクトルのプロトタイプ。これのコピーが保存され、外挿値がそこに書き込まれます。指定されていない場合、コールバックのすべての適用で状態ベクトルの新しいコピーが割り当てられます。

## キーワード引数

  * `save`: 標準の保存を行うかどうか（コールバックの後に適用されます）。
  * `abstol`: 残差が受け入れられるまでの許容範囲。要素ごとの許容範囲が許可されています。指定されていない場合、コールバックのすべての適用で積分器の現在の絶対許容範囲が使用されます。
  * `scalefactor`: 受け入れられない時間ステップが減少する係数。指定されていない場合、時間ステップは半分になります。
  * `autonomous`: `g` が `g(resid, u, p)` の形の自律関数であるかどうか。指定されていない場合、自動的に決定されます。
  * `kwargs`: その他のすべてのキーワード引数は [`ManifoldProjection`](@ref) に渡されます。
  * `nlsolve_kwargs`: すべてのキーワード引数は `ManifoldProjection` の非線形ソルバーに渡されます。デフォルトは `(; abstol = 10 * eps())` です。
  * `domain_jacobian`: ドメインのヤコビアン（状態に関して）。これは `g` と同じシグネチャを持ち、最初の引数はインプレースの場合のヤコビアンです。これは [`ManifoldProjection`](@ref) の `manifold_jacobian` 引数に対応します。`GeneralDomain` に対して `manifold_jacobian` を渡すことはサポートされておらず、エラーが発生します。

## 参考文献

Shampine, Lawrence F., Skip Thompson, Jacek Kierzenka and G. D. Byrne. Non-negative solutions of ODEs. Applied Mathematics and Computation 170 (2005): 556-569.
