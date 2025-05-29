```
struct TimeEvolutionHEOMSol
```

階層運動方程式 (HEOM) の時間発展を解く際の結果といくつかの情報を格納する構造体です。

# フィールド (属性)

  * `Btier` : ボソン階層のティア (カットオフレベル)
  * `Ftier` : フェルミオン階層のティア (カットオフレベル)
  * `times::AbstractVector`: 発展の時間リスト。
  * `ados::Vector{ADOs}`: 各時間点での結果 ADO のリスト。
  * `expect::Matrix`: `times` の各時間点に対応する期待値。
  * `retcode`: ソルバーからの戻りコード。
  * `alg`: 解決プロセス中に使用されるアルゴリズム。
  * `abstol::Real`: 解決プロセス中に使用される絶対許容誤差。
  * `reltol::Real`: 解決プロセス中に使用される相対許容誤差。
