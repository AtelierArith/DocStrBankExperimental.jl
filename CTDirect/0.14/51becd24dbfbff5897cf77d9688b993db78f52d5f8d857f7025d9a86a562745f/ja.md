```julia
direct_transcription(
    ocp::CTModels.Model,
    description...;
    grid_size,
    disc_method,
    time_grid,
    init,
    adnlp_backend,
    solver_backend,
    show_time,
    matrix_free
) -> Tuple{CTDirect.DOCP{_A, CTModels.Model{TimesModelType, StateModelType, ControlModelType, VariableModelType, DynamicsModelType, ObjectiveModelType, ConstraintsModelType}} where {_A<:CTDirect.Discretization, TimesModelType<:CTModels.AbstractTimesModel, StateModelType<:CTModels.AbstractStateModel, ControlModelType<:CTModels.AbstractControlModel, VariableModelType<:CTModels.AbstractVariableModel, DynamicsModelType<:Function, ObjectiveModelType<:CTModels.AbstractObjectiveModel, ConstraintsModelType<:CTModels.AbstractConstraintsModel}, ADNLPModels.ADNLPModel{Float64, Vector{Float64}, Vector{Int64}}}

```

最適制御問題を非線形最適化問題に離散化します（すなわち、直接転写）

# 引数

  * ocp: `CTModels`で定義された最適制御問題
  * [description]: NLPモデルやソルバー（:ipopt、:madnlp、または:knitro）を指定できます

# キーワード引数（オプション）

  * `grid_size`: 離散化された問題の時間ステップ数（[250]）
  * `disc_method`: 離散化方法（[`:trapeze`], `:euler`, `:euler_implicit`, `:midpoint`, `gauss_legendre_2`, `gauss_legendre_3`）
  * `time_grid`: 明示的な時間グリッド（非一様でも可）
  * `init`: 開始推測のための情報（名前付きタプルまたは既存の解としての値）
  * `adnlp_backend`: ADNLPModelsにおける自動微分のバックエンド（[`:optimized`], `:manual`, `:default`）
  * show_time: (:true, [:false]) ADNLPModelsからのタイミング詳細を表示
