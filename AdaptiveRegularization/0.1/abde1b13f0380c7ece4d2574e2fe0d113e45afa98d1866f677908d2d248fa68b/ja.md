```
TRARC(nlp; kwargs...)
```

信頼領域（TR）/適応正則化と立方体（ARC）法を使用して、制約のない最適化問題の局所最小値を計算します。

TRARCのいくつかのバリアントはすでに実装されており、`AdaptiveRegularization.ALL_solvers`にリストされています。

# 引数

  * `nlp::AbstractNLPModel`: 解決されるモデル、`NLPModels.jl`を参照してください。

キーワード引数には以下が含まれます。

  * `TR::ARTrustRegion`: 信頼領域/ARCパラメータを持つ構造体、[`SolverTools.jl`](https://github.com/JuliaSmoothOptimizers/SolverTools.jl)を参照してください。デフォルト: `ARTrustRegion(T(10.0))`。
  * `hess_type::Type{Hess}`: ヘッセ行列を処理するために使用される構造体。可能な値は次のとおりです: `HessDense`, `HessSparse`, `HessSparseCOO`, `HessOp`。デフォルト: `HessOp`。
  * `pdata_type::Type{ParamData}`: 前処理ステップに使用される構造体。デフォルト: `PDataKARC`。
  * `robust::Bool`: `true`はモデルの堅牢な評価を実装します。デフォルト: `true`。
  * `verbose::Bool`: `true`は反復情報を出力します。デフォルト: `false`。

追加の`kwargs`は停止基準に使用されます。`Stopping.jl`を参照してください。

# 出力

返される値は`GenericExecutionStats`です。`SolverCore.jl`を参照してください。

# コールバック

コールバックは各反復で呼び出されます。コールバックの期待されるシグネチャは`callback(nlp, solver, stats)`であり、その出力は無視されます。入力引数のいずれかを変更すると、次の反復に影響を与えます。特に、`stats.status = :user`を設定すると、アルゴリズムが停止します。すべての関連情報は`nlp`と`solver`で利用可能であるべきです。特に、以下にアクセスし、変更できます。

  * `solver.stp`: アルゴリズムに使用される停止オブジェクト；
  * `solver.workspace`: 追加の割り当て；
  * `stats`: アルゴリズムの出力を保持する構造体（`GenericExecutionStats`）、その中には以下の情報が含まれます：

      * `stats.dual_feas`: 現在の勾配のノルム；
      * `stats.iter`: 現在の反復カウンタ；
      * `stats.objective`: 現在の目的関数の値；
      * `stats.status`: アルゴリズムの現在の状態。アルゴリズムが停止基準に達していない限り、`:unknown`であるべきです。これを何かに変更するとアルゴリズムが停止しますが、意図を適切に示すために`:user`を使用するべきです。
      * `stats.elapsed_time`: 経過時間（秒）。

この実装は`Stopping.jl`を使用しています。したがって、次のように使用することも可能です。

```
TRARC(stp; kwargs...)
```

これにより、`stp::NLPStopping`が更新されて返されます。

高度な使用法では、最初に[`TRARCSolver`](@ref)を定義してアルゴリズムで使用されるメモリを事前に割り当て、その後`solve!`を呼び出します：

```
stats = solve!(solver, nlp)
stats = solve!(solver, nlp, stats)
```

特定のバリアントを選択するには、キーワード引数`hess_type`と`pdata_type`を次のように使用できます：`TRARCSolver(nlp; hess_type = ht, pdata_type = PDataKARC)`。前者はヘッセ行列情報の処理方法、すなわち行列フリーまたはスパース行列を指定し、後者は適応アプローチのタイプ、例えば信頼領域またはARCを指定します。

# 参考文献

このメソッドは、信頼領域と立方体による適応正則化の実装を統一します。

```
Dussault, J.-P. (2020).
A unified efficient implementation of trust-region type algorithms for unconstrained optimization.
INFOR: Information Systems and Operational Research, 58(2), 290-309.
10.1080/03155986.2019.1624490
```

# 例

```jldoctest
using AdaptiveRegularization, ADNLPModels
nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0]);
stats = TRARC(nlp)

# 出力

"実行統計: 一次の定常状態"
```

```jldoctest; output = false
using AdaptiveRegularization, ADNLPModels, SolverCore
nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0]);
solver = TRARCSolver(nlp);
stats = solve!(solver, nlp)

# 出力

"実行統計: 一次の定常状態"
```

```jldoctest; output = false
using AdaptiveRegularization, ADNLPModels, SolverCore
nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0]);
solver = TRARCSolver(nlp);
stats = GenericExecutionStats(nlp)
stats = solve!(solver, nlp, stats)

# 出力

"実行統計: 一次の定常状態"
```
