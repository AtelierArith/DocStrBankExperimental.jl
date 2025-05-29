可変構造体で、ソルバーのパラメータを保持します。

```
SolverParameters{F <: AbstractFloat, I <: Integer}
```

# フィールド

  * `solver::OrdinaryDiffEq.OrdinaryDiffEqAdaptiveAlgorithm`: 微分方程式を解くために使用されるアルゴリズム。
  * `reltol::F`: ソルバーの相対許容誤差。
  * `step::F`: ソルバーのステップサイズ。
  * `tstops::Union{Nothing, Vector{F}}`: コールバックのためにソルバーが停止すべき時間点のオプションベクター。
  * `save_everystep::Bool`: 各ステップで解を保存するかどうかを示すフラグ。
  * `progress::Bool`: 解決プロセス中に進行状況を表示するかどうかを示すフラグ。
  * `progress_steps::I`: 進行状況の更新間のステップ数。
