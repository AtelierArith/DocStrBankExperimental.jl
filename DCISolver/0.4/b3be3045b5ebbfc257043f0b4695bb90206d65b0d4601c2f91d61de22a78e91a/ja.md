```
dci(nlp; kwargs...)
dci(nlp, x; kwargs...)
dci(nlp, meta, x)
```

Bielschowsky & Gomes (2008) の DCI アルゴリズムを使用して、等式制約付き最適化問題の局所最小値を計算します。

# 引数

  * `nlp::AbstractNLPModel`: 解決されるモデル、`NLPModels.jl` を参照してください。
  * `x`: 初期推定値。`x` が指定されていない場合、`nlp.meta.x0` が使用されます。
  * `meta`: キーワード引数は [`MetaDCI`](@ref) を初期化するために使用されます。

高度な使用法では、ソルバーへの主な呼び出しは [`DCIWorkspace`](@ref) を使用します。

```
solve!(workspace, nlp)
solve!(workspace, nlp, stats)
```

# 出力

返される値は `GenericExecutionStats` であり、`SolverCore.jl` を参照してください。

# コールバック

コールバックは各イテレーションで呼び出されます。コールバックの期待されるシグネチャは `callback(nlp, workspace, stats)` であり、その出力は無視されます。入力引数のいずれかを変更すると、次のイテレーションに影響を与えます。特に、`stats.status = :user` を設定するとアルゴリズムが停止します。関連するすべての情報は `nlp` と `workspace` で利用可能であるべきです。特に、以下にアクセスし、変更することができます：

  * `workspace`: 現在のワークスペース；
  * `stats`: アルゴリズムの出力を保持する構造体 (`GenericExecutionStats`)、その中には以下のものが含まれます：

      * `stats.dual_feas`: 現在の勾配のノルム；
      * `stats.iter`: 現在のイテレーションカウンタ；
      * `stats.objective`: 現在の目的関数の値；
      * `stats.status`: アルゴリズムの現在の状態。アルゴリズムが停止基準に達していない限り `:unknown` であるべきです。これを何かに変更するとアルゴリズムが停止しますが、意図を適切に示すために `:user` を使用するべきです。
      * `stats.elapsed_time`: 経過時間（秒）。

# 参考文献

このメソッドは、以下に記載された等式制約付き問題のための不適合性の動的制御を実装しています。

```
Dynamic Control of Infeasibility in Equality Constrained Optimization
Roberto H. Bielschowsky and Francisco A. M. Gomes
SIAM J. Optim., 19(3), 2008, 1299–1325.
https://doi.org/10.1137/070679557
```

# 例

```jldoctest; output = false
using ADNLPModels, DCISolver
nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0])
stats = dci(nlp, verbose = 0)
stats

# output

"Execution stats: first-order stationary"
```
