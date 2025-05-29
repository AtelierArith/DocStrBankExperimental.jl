`SolverParameters`オブジェクトを指定されたパラメータで構築するか、デフォルト値を使用します。

```
SolverParameters(; solver::OrdinaryDiffEq.OrdinaryDiffEqAdaptiveAlgorithm = RDPK3Sp35(),
                  reltol::F = 1e-12,
                  step::F = 1.0/12.0,
                  tstops::Union{Nothing,Vector{F}} = nothing,
                  save_everystep = false,
                  progress::Bool = true,
                  progress_steps::I = 10) where {F <: AbstractFloat, I <: Integer}
```

# 引数

  * `solver::OrdinaryDiffEq.OrdinaryDiffEqAdaptiveAlgorithm`: 使用するODEソルバーアルゴリズム。デフォルトは`RDPK3Sp35()`です。
  * `reltol::F`: ソルバーの相対許容誤差。デフォルトは`1e-12`です。
  * `step::F`: コールバックのステップサイズ。これらは主に表面質量バランスモデルを実行するために使用されます。デフォルトは`1.0/12.0`（すなわち1か月）です。
  * `tstops::Union{Nothing, Vector{F}}`: ソルバーが停止すべき時間点のオプションベクター。デフォルトは`nothing`です。
  * `save_everystep::Bool`: すべてのステップで解を保存するかどうか。デフォルトは`false`です。
  * `progress::Bool`: 解決プロセス中に進捗を表示するかどうか。デフォルトは`true`です。
  * `progress_steps::I`: 進捗更新の間のステップ数。デフォルトは`10`です。

# 戻り値

  * `solver_parameters`: 指定されたパラメータで構築された`SolverParameters`オブジェクト。
