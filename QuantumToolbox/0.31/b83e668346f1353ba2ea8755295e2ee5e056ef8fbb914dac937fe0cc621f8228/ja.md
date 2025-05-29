```
struct TimeEvolutionSol
```

時間発展を解く際の結果といくつかの情報を格納する構造体です。

# フィールド（属性）

  * `times::AbstractVector`: 発展の時間リスト。
  * `states::Vector{QuantumObject}`: 結果状態のリスト。
  * `expect::Union{AbstractMatrix,Nothing}`: `times`の各時間点に対応する期待値。
  * `retcode`: ソルバーからの戻りコード。
  * `alg`: 解決プロセス中に使用されるアルゴリズム。
  * `abstol::Real`: 解決プロセス中に使用される絶対許容誤差。
  * `reltol::Real`: 解決プロセス中に使用される相対許容誤差。
