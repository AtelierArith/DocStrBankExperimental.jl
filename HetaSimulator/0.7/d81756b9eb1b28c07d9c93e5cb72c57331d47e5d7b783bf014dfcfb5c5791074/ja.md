```
fit(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::AbstractVector{<:Pair{Symbol,<:Real}};
  parameters::Union{Nothing, Vector{P}}=nothing,
  alg=DEFAULT_ALG,
  reltol=DEFAULT_FITTING_RELTOL,
  abstol=DEFAULT_FITTING_ABSTOL,
  parallel_type=EnsembleSerial(),
  ftol_abs = 0.0,
  ftol_rel = 1e-4, 
  xtol_rel = 0.0,
  xtol_abs = 0.0, 
  fit_alg = :LN_NELDERMEAD,
  maxeval = 10000,
  maxtime = 0.0,
  lbounds = fill(0.0, length(parameters_fitted)),
  ubounds = fill(Inf, length(parameters_fitted)),
  scale = fill(:lin, length(parameters_fitted)),
  progress::Symbol = :minimal,
  kwargs... 
) where {C<:AbstractScenario, P<:Pair}
```

実験測定にパラメータをフィットします。`FitResult`型を返します。

例: `fit([:x=>scn2, :y=>scn3, :z=>scn4], [:k1=>0.1,:k2=>0.2,:k3=>0.3])`

引数:

  * `scenario_pairs` : 名前と[`Scenario`](@ref)のタイプのシナリオを含むペアのベクター
  * `parameters_fitted` : 最適化パラメータとその初期値
  * `parameters` : `Model`と`Scenario`のパラメータを上書きするパラメータ。デフォルトは`nothing`
  * `alg` : ODEソルバー。詳細についてはSciMLのドキュメントを参照してください。デフォルトはAutoTsit5(Rosenbrock23())
  * `reltol` : 相対許容誤差。デフォルトは1e-6
  * `abstol` : 絶対許容誤差。デフォルトは1e-8
  * `parallel_type` : 並列設定。詳細についてはSciMLのドキュメントを参照してください。デフォルトは並列処理なし: EnsembleSerial()
  * `ftol_abs` : 関数値の絶対許容誤差。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`0.0`
  * `ftol_rel` : 関数値の相対許容誤差。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`1e-4`
  * `xtol_rel` : 最適化パラメータの相対許容誤差。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`0.0`
  * `xtol_abs` : 最適化パラメータの絶対許容誤差。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`0.0`
  * `fit_alg` : フィッティングアルゴリズム。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`:LN_NELDERMEAD`
  * `maxeval` : 関数評価の最大数。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`1e4`
  * `maxtime` : 最大最適化時間（秒単位）。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`0`
  * `lbounds` : 下限パラメータの境界。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`fill(0.0, length(parameters_fitted))`
  * `ubounds` : 上限パラメータの境界。詳細については`NLopt.jl`のドキュメントを参照してください。デフォルトは`fill(Inf, length(parameters_fitted))`
  * `scale`   : フィッティング中に使用されるパラメータのスケール（`:lin, :direct, :log, :log10`をサポート）。デフォルトは`fill(:lin, length(parameters_fitted))`。`:direct`の値は`:lin`の同義語です。
  * `progress` : 進行状況モードの表示。3つの値のいずれか: `:silent`, `:minimal`, `:full`。デフォルトは`:minimal`
  * `kwargs...` : SciMLBase.solveによってサポートされる他のソルバー関連の引数。詳細についてはSciMLのドキュメントを参照してください。
