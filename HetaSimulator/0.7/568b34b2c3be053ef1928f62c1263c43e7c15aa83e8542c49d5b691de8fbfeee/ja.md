```
function estimator(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::AbstractVector{<:Pair{Symbol,<:Real}};
  parameters::Union{Nothing, Vector{P}}=nothing,
  alg=DEFAULT_ALG,
  reltol=DEFAULT_FITTING_RELTOL,
  abstol=DEFAULT_FITTING_ABSTOL,
  parallel_type=EnsembleSerial(),
  kwargs... # 他の引数をsimに渡す
) where {C<:AbstractScenario, P<:Pair}
```

パラメータの特定と分析のための尤度推定器関数を生成します。これは、パラメータセットに依存する関数としての `-2ln(L)` に対応します。

例: `estimator([:x=>scn2, :y=>scn3, :z=>scn4], [:k1=>0.1,:k2=>0.2,:k3=>0.3])`

引数:

  * `scenario_pairs` : [`Scenario`](@ref) 型の名前とシナリオを含むペアのベクター
  * `parameters_fitted` : デフォルトとして使用されるパラメータとその名目値
  * `parameters` : `Model` と `Scenario` のパラメータの両方を上書きするパラメータ。デフォルトは `nothing`
  * `alg` : ODE ソルバー。詳細については SciML ドキュメントを参照してください。デフォルトは AutoTsit5(Rosenbrock23())
  * `reltol` : 相対許容誤差。デフォルトは 1e-6
  * `abstol` : 絶対許容誤差。デフォルトは 1e-8
  * `parallel_type` : 並列設定。詳細については SciML ドキュメントを参照してください。デフォルトは並列処理なし: EnsembleSerial()
  * `kwargs...` : `SciMLBase.solve` によってサポートされる他の ODE ソルバー関連の引数。詳細については SciML ドキュメントを参照してください

戻り値:

```
function(x:Vector{Float64}=last.(parameters_fitted))
```

このメソッドは、`parameters_fitted` と同じ順序でパラメータベクターに依存する匿名関数を返します。この関数は、最適化ルーチンや同定可能性分析に渡す準備が整っています。
