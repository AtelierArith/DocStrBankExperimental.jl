```
build_settings(
    eng::Dict{String,<:Any};
    max_switch_actions::Union{Missing,Int,Vector{Int}},
    vm_lb_pu::Union{Missing,Real}=missing,
    vm_ub_pu::Union{Missing,Real}=missing,
    vad_deg::Union{Missing,Real}=missing,
    line_limit_mult::Real=1.0,
    sbase_default::Union{Missing,Real}=missing,
    time_elapsed::Union{Missing,Real,Vector{Real}}=missing,
    autogen_microgrid_ids::Bool=true,
    custom_settings::Dict{String,<:Any}=Dict{String,Any}(),
    mip_solver_gap::Real=0.05,
    nlp_solver_tol::Real=1e-4,
    mip_solver_tol::Real=1e-4,
    clpu_factor::Union{Missing,Real}=missing,
    disable_switch_penalty::Bool=false,
    apply_switch_scores::Bool=false,
    disable_radial_constraint::Bool=false,
    disable_isolation_constraint::Bool=false,
    disable_inverter_constraint::Bool=false,
    storage_phase_unbalance_factor::Union{Missing,Real}=missing,
    disable_presolver::Bool=false,
)::Dict{String,Any}
```

**非推奨**: この関数は [`build_settings_new`](build_settings_new) に置き換えられました。

ONMで使用するための設定ファイル（json）を構築するためのヘルパー関数です。プロパティが `missing` の場合、それらは設定されません。

  * `network_file::String` は入力ネットワークファイル（dss）へのパスです。
  * `settings_file::String` は出力設定ファイル（json）へのパスです。
  * `max_switch_actions::Union{Int,Vector{Int}}` は、最大で各時間ステップごとに実行できるアクションの数を指定するために使用できます。特にスイッチクローズアクションに関連します。単一の整数として指定することも、リストとして指定することもできます（デフォルト: `missing`）。
  * `vm_lb_pu::Real` は、各バスの下限電圧をパー・ユニットで指定するために使用できます（デフォルト: `missing`）。
  * `vm_ub_pu::Real` は、各バスの上限電圧をパー・ユニットで指定するために使用できます（デフォルト: `missing`）。
  * `vad_deg::Real` は、各ラインの下限/上限（0.0の周りの範囲）を度で指定するために使用できます（デフォルト: `missing`）。
  * `line_limit_mult::Real` は、各ライン、スイッチ、および変圧器の電力/電流定格に乗算係数を適用するために使用できます（デフォルト: `1.0`）。
  * `sbase_default::Real` は、パー・ユニットに変換するために使用されるsbase係数を調整するために使用できます。これにより、最適化の安定性が向上する可能性があります（デフォルト: `missing`）。
  * `time_elapsed::Union{Real,Vector{Real}}` は、時間ステップの期間を調整するために使用できます。単一の数値として指定することも、リストとして指定することもできます（デフォルト: `missing`）。
  * `autogen_microgrid_ids::Bool` は、ONMアルゴリズムおよび統計分析で使用されるマイクログリッドの「ID」の自動生成を切り替えます（デフォルト: `missing`）。
  * `custom_settings:Dict{String,Any}` は、すべての自動生成された設定が作成された後に適用されるカスタム設定を渡すために使用できます（したがって、競合する自動生成設定を再帰的にマージして上書きします）。
  * `mip_solver_gap::Real` は、MIPソルバーの許容ギャップを調整するために使用できます（デフォルト: `0.05`、すなわち5%）。
  * `nlp_solver_tol::Real` は、NLPソルバーにおける制約違反の許容誤差を調整するために使用できます（デフォルト: `0.0001`）。
  * `mip_solver_tol::Real` は、MIPソルバーにおける制約違反の許容誤差を調整するために使用できます（デフォルト: `0.0001`）。
  * `clpu_factor::Real` は、コールドロードピックアップ推定のための係数を設定するために使用できます（デフォルト: missing）。
  * `disable_switch_penalty::Bool` は、目的関数におけるスイッチアクションに適用されるペナルティを無効にするためのトグルです（デフォルト: `false`）。
  * `apply_switch_scores::Bool` は、目的関数に適用されるスイッチアクションの重みを有効にするためのトグルです（デフォルト: `false`）。
  * `disable_radial_constraint::Bool` は、スイッチング問題における放射制約を無効にするためのトグルです（デフォルト: `false`）。
  * `disable_isolation_constraint::Bool` は、スイッチング問題におけるブロック隔離制約を無効にするためのトグルです（デフォルト: `false`）。
  * `disable_presolver::Bool` は、それをサポートする組み込みソルバー（Gurobi、KNITRO）でのプレソルバーを無効にするためのトグルです（デフォルト: `false`）。
  * `storage_phase_unbalance_factor::Real` は、すべてのストレージデバイスに対して `phase_unbalance_factor` を設定する方法です（デフォルト: `missing`）。
