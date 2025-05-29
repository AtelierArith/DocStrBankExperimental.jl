```
struct TimeEvolutionStochasticSol
```

確率的時間発展の軌道を解く際の結果といくつかの情報を格納する構造体です。

# フィールド（属性）

  * `ntraj::Int`: 軌道の数
  * `times::AbstractVector`: 発展の時間リスト。
  * `states::Vector{Vector{QuantumObject}}`: 各軌道における結果状態のリスト。
  * `expect::Union{AbstractMatrix,Nothing}`: `times`の各時間点に対応する期待値（すべての軌道を平均したもの）。
  * `average_expect::Union{AbstractMatrix,Nothing}`: `times`の各時間点に対応する期待値（すべての軌道を平均したもの）。
  * `runs_expect::Union{AbstractArray,Nothing}`: `times`の各時間点および各軌道に対応する期待値
  * `converged::Bool`: 解が収束しているかどうか。
  * `alg`: 解決プロセス中に使用されるアルゴリズム。
  * `abstol::Real`: 解決プロセス中に使用される絶対許容誤差。
  * `reltol::Real`: 解決プロセス中に使用される相対許容誤差。
