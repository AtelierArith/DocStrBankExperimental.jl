```
struct TimeEvolutionLRSol
```

低ランクマスター方程式の時間発展を解く際の結果と情報を格納する構造体です。

# フィールド（属性）

  * `times::AbstractVector`: 発展の時間リスト。
  * `states::Vector{QuantumObject}`: 結果の状態のリスト。
  * `expect::Matrix`: `times`の各時間点に対応する期待値。
  * `fexpect::Matrix`: 各時間点での関数値。
  * `retcode`: ソルバーからの戻りコード。
  * `alg`: 解決プロセス中に使用されるアルゴリズム。
  * `abstol::Real`: 解決プロセス中に使用される絶対許容誤差。
  * `reltol::Real`: 解決プロセス中に使用される相対許容誤差。
  * `z::Vector{QuantumObject}`: 各時間点での低ランクアルゴリズムの`z`行列。
  * `B::Vector{QuantumObject}`: 各時間点での低ランクアルゴリズムの`B`行列。
