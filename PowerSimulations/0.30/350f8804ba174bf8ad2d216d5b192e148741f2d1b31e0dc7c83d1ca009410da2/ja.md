```
DecisionModel{M}(
    template::AbstractProblemTemplate,
    sys::PSY.System,
    jump_model::Union{Nothing, JuMP.Model}=nothing;
    kwargs...) where {M<:DecisionProblem}
```

特定のシステムとテンプレートを使用して、タイプ M の最適化問題を構築します。

# 引数

  * `::Type{M} where M<:DecisionProblem`: 抽象操作モデルのタイプ
  * `template::AbstractProblemTemplate`: 伝送、デバイス、ブランチ、およびサービスで構成されるモデル参照。
  * `sys::PSY.System`: Power Systems を使用して作成されたシステム
  * `jump_model::Union{Nothing, JuMP.Model}`: カスタム JuMP モデルを渡すことを可能にします。注意して使用してください。
  * `name = nothing`: モデルの名前、文字列またはシンボル; デフォルトはテンプレートのタイプをシンボルに変換したものです。
  * `optimizer::Union{Nothing,MOI.OptimizerWithAttributes} = nothing` : オプティマイザはシリアライズされません。呼び出し元は元の問題に渡したものを渡す必要があります。
  * `horizon::Dates.Period = UNSET_HORIZON`: 予測ホライズンの長さを手動で指定します。
  * `resolution::Dates.Period = UNSET_RESOLUTION`: モデルの解像度を手動で指定します。
  * `warm_start::Bool = true`: True は、システム内の現在の操作点を使用して変数の値を初期化します。False はすべての変数をゼロに初期化します。デフォルトは true です。
  * `system_to_file::Bool = true:`: モデルで使用されるシステムのコピーを作成するために True。
  * `initialize_model::Bool = true`: モデルを初期化するかどうかを決定するオプション。
  * `initialization_file::String = ""`: これは、最適化問題の解決を回避するために、既存の初期化値を渡すことを可能にします。
  * `deserialize_initial_conditions::Bool = false`: 条件をデシリアライズするオプション
  * `export_pwl_vars::Bool = false`: すべての pwl 中間変数をエクスポートするために True。ビルドと解決の時間が大幅に遅くなる可能性があります。
  * `allow_fails::Bool = false`: 最適化ステップが失敗してもシミュレーションを続行することを許可するために True。注意して使用してください。
  * `optimizer_solve_log_print::Bool = false`: JuMP.unset_silent() を使用してオプティマイザのログを印刷します。デフォルトではすべてのソルバーは MOI.Silent() に設定されています。
  * `detailed_optimizer_stats::Bool = false`: 詳細なオプティマイザ統計ログを保存するために True。
  * `calculate_conflict::Bool = false`: 不 feasible な問題のためにソルバーを使用して衝突を計算するために True。特定のソルバーのみが衝突を計算できます。
  * `direct_mode_optimizer::Bool = false`: ソルバーを直接モードで使用するために True。 [JuMP.direct_model](https://jump.dev/JuMP.jl/dev/reference/models/#JuMP.direct_model) を作成します。
  * `store_variable_names::Bool = false`: 最適化モデルに変数名を保存するために。ビルド時間が短縮されます。
  * `rebuild_model::Bool = false`: モデルを更新するたびに基盤となる JuMP モデルの再構築を強制します。解決時間が増加しますので、メモリ内でモデルを更新できない場合のみ使用してください。
  * `initial_time::Dates.DateTime = UNSET_INI_TIME`: モデル解決の初期時間。
  * `time_series_cache_size::Int = IS.TIME_SERIES_CACHE_SIZE_BYTES`: 各時間配列のキャッシュサイズ（バイト単位）。デフォルトは 1 MiB です。無効にするには 0 に設定します。

# 例

```julia
template = ProblemTemplate(CopperPlatePowerModel, devices, branches, services)
OpModel = DecisionModel(MockOperationProblem, template, system)
```
