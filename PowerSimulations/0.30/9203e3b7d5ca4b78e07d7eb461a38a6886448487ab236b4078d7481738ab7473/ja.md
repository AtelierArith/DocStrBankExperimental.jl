```
EmulationModel{M}(
    template::AbstractProblemTemplate,
    sys::PSY.System,
    jump_model::Union{Nothing, JuMP.Model}=nothing;
    kwargs...) where {M<:EmulationProblem}
```

特定のシステムとテンプレートを使用して、タイプ M の最適化問題を構築します。

# 引数

  * `::Type{M} where M<:EmulationProblem`: 抽象エミュレーションモデルタイプ
  * `template::AbstractProblemTemplate`: 伝送、デバイス、ブランチ、およびサービスで構成されるモデル参照。
  * `sys::PSY.System`: Power Systems を使用して作成されたシステム
  * `jump_model::Union{Nothing, JuMP.Model}`: カスタム JuMP モデルを渡すことを可能にします。注意して使用してください。
  * `name = nothing`: モデルの名前、文字列またはシンボル; デフォルトはテンプレートのタイプをシンボルに変換したものです。
  * `optimizer::Union{Nothing,MOI.OptimizerWithAttributes} = nothing` : オプティマイザはシリアライズされません。呼び出し元は元の問題に渡したものを渡す必要があります。
  * `warm_start::Bool = true`: True は、システム内の現在の操作点を使用して変数値を初期化します。False はすべての変数をゼロに初期化します。デフォルトは true です。
  * `system_to_file::Bool = true:`: モデルで使用されるシステムのコピーを作成するには True にします。
  * `initialize_model::Bool = true`: モデルを初期化するかどうかを決定するオプション。
  * `initialization_file::String = ""`: これは、最適化問題の解決を回避するために、既存の初期化値を渡すことを可能にします。
  * `deserialize_initial_conditions::Bool = false`: 条件をデシリアライズするオプション
  * `export_pwl_vars::Bool = false`: True はすべての pwl 中間変数をエクスポートします。ビルドと解決時間が大幅に遅くなる可能性があります。
  * `allow_fails::Bool = false`: True は、最適化ステップが失敗してもシミュレーションを続行できるようにします。注意して使用してください。
  * `calculate_conflict::Bool = false`: True は、解決不可能な問題のためにソルバーを使用して矛盾を計算します。特定のソルバーのみが矛盾を計算できます。
  * `optimizer_solve_log_print::Bool = false`: JuMP.unset_silent() を使用してオプティマイザのログを印刷します。デフォルトではすべてのソルバーは MOI.Silent() に設定されています。
  * `detailed_optimizer_stats::Bool = false`: True は詳細なオプティマイザ統計ログを保存します。
  * `direct_mode_optimizer::Bool = false`: True は、ソルバーを直接モードで使用します。[JuMP.direct_model](https://jump.dev/JuMP.jl/dev/reference/models/#JuMP.direct_model) を作成します。
  * `store_variable_names::Bool = false`: True は、最適化モデルに変数名を保存します。
  * `rebuild_model::Bool = false`: モデルを更新するたびに基盤となる JuMP モデルの再構築を強制します。解決時間が増加しますので、メモリ内でモデルを更新できない場合のみ使用してください。
  * `initial_time::Dates.DateTime = UNSET_INI_TIME`: モデル解決の初期時間。
  * `time_series_cache_size::Int = IS.TIME_SERIES_CACHE_SIZE_BYTES`: 各時間配列のキャッシュサイズ（バイト単位）。デフォルトは 1 MiB です。無効にするには 0 に設定します。

# 例

```julia
template = ProblemTemplate(CopperPlatePowerModel, devices, branches, services)
OpModel = EmulationModel(MockEmulationProblem, template, system)
```
