```
stats_ps = presolve(qm::QuadraticModel{T, S}; fixed_vars_only = false, kwargs...)
```

`qm`に対して前処理ルーチンを適用し、パッケージ[`SolverCore.jl`](https://github.com/JuliaSmoothOptimizers/SolverCore.jl)からの[`GenericExecutionStats`](https://juliasmoothoptimizers.github.io/SolverCore.jl/stable/reference/#SolverCore.GenericExecutionStats)を返します。現在実装されている前処理操作は以下の通りです：

  * 空の行を削除
  * 単一行を削除
  * 線形制約のない変数を固定（lps）
  * ヘッセ行列に現れない関連変数を持つ自由線形単一列を削除
  * 固定変数を削除

`PresolvedQuadraticModel{T, S} <: AbstractQuadraticModel{T, S}`は`solver_specific`フィールドにあります：

```
psqm = stats_ps.solver_specific[:presolvedQM]
```

そして、[`postsolve`](@ref)を呼び出すために使用されるべきです。固定変数のみを削除したい場合は、`fixed_vars_only = true`を使用してください。最大化問題は最小化問題に変換されます。前処理された最大化問題の目的が必要な場合は、前処理された問題の目的の反対を取ることを確認してください。

前処理された問題に変数が0の場合、`stats_ps.solution`には原問題の解が含まれ、`stats_ps.multipliers`はゼロの`SparseVector`であり、もし次のように定義すると

```
s = qm.data.c + qm.data.H * stats_ps.solution
```

`stats_ps.multipliers_L`は`s`の正の部分であり、`stats_ps.multipliers_U`は`s`の負の部分の反対です。前処理操作は[`MathOptPresolve.jl`](https://github.com/mtanneau/MathOptPresolve.jl)および以下からインスパイアを受けています：

  * Gould, N., Toint, P. [*Preprocessing for quadratic programming*](https://doi.org/10.1007/s10107-003-0487-2), Math. Program., Ser. B 100, 95–132 (2004).
