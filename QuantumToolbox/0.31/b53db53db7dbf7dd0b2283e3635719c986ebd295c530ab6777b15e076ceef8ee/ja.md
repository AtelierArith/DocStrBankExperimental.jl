```
struct TimeEvolutionMCSol
```

量子トラジェクトリのモンテカルロ波動関数の時間発展を解く際の結果と情報を格納する構造体です。

# フィールド（属性）

  * `ntraj::Int`: トラジェクトリの数
  * `times::AbstractVector`: 発展の時間リスト。
  * `states::Vector{Vector{QuantumObject}}`: 各トラジェクトリにおける結果状態のリスト。
  * `expect::Union{AbstractMatrix,Nothing}`: `times`の各時間点に対応する期待値（すべてのトラジェクトリを平均したもの）。
  * `average_expect::Union{AbstractMatrix,Nothing}`: `times`の各時間点に対応する期待値（すべてのトラジェクトリを平均したもの）。
  * `runs_expect::Union{AbstractArray,Nothing}`: `times`の各時間点および各トラジェクトリに対応する期待値
  * `col_times::Vector{Vector{Real}}`: 各トラジェクトリで発生したすべての量子ジャンプの時間記録。
  * `col_which::Vector{Vector{Int}}`: `col_times`の各量子ジャンプに対してどの崩壊演算子が責任を持っていたかのインデックス。
  * `converged::Bool`: 解が収束しているかどうか。
  * `alg`: 解決プロセス中に使用されるアルゴリズム。
  * `abstol::Real`: 解決プロセス中に使用される絶対許容誤差。
  * `reltol::Real`: 解決プロセス中に使用される相対許容誤差。
