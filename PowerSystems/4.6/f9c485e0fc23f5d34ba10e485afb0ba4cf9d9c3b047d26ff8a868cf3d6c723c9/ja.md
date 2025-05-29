```
mutable struct ReactiveRenewableControllerAB <: ReactivePowerControl
    bus_control::Int
    from_branch_control::Int
    to_branch_control::Int
    branch_id_control::String
    VC_Flag::Int
    Ref_Flag::Int
    PF_Flag::Int
    V_Flag::Int
    T_fltr::Float64
    K_p::Float64
    K_i::Float64
    T_ft::Float64
    T_fv::Float64
    V_frz::Float64
    R_c::Float64
    X_c::Float64
    K_c::Float64
    e_lim::MinMax
    dbd_pnts::Tuple{Float64, Float64}
    Q_lim::MinMax
    T_p::Float64
    Q_lim_inner::MinMax
    V_lim::MinMax
    K_qp::Float64
    K_qi::Float64
    Q_ref::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end

Reactive Power ControllerのパラメータにはREPCA1とREECB1が含まれます

# 引数

  * `bus_control::Int`: 電圧制御のためのACBus識別[`number`](@ref ACBus)。`0`はこのコンポーネントに接続されたローカルバスを識別し、検証範囲: `(0, nothing)`
  * `from_branch_control::Int`: ラインドロップ補償のための監視されたブランチFROMバス識別番号（0の場合は発電機の電力が使用されます）、検証範囲: `(0, nothing)`
  * `to_branch_control::Int`: ラインドロップ補償のための監視されたブランチTOバス識別番号（0の場合は発電機の電力が使用されます）、検証範囲: `(0, nothing)`
  * `branch_id_control::String`: ラインドロップ補償のためのブランチ回路ID（文字列として）。0の場合は発電機の電力が使用されます
  * `VC_Flag::Int`: REPCA1の電圧補償器フラグ、検証範囲: `(0, 1)`
  * `Ref_Flag::Int`: REPCA1のための無効電力制御フラグ。0: Q制御、1: V制御、検証範囲: `(0, 1)`
  * `PF_Flag::Int`: REECB1の外部制御のための力率制御フラグ。0: Q制御、1: 力率制御、検証範囲: `(0, 1)`
  * `V_Flag::Int`: REECB1の外部制御のための電圧制御フラグ。0: 電圧制御、1: Q制御、検証範囲: `(0, 1)`
  * `T_fltr::Float64`: REPCAフィルターの電圧またはQ電力の時間定数、検証範囲: `(0, nothing)`
  * `K_p::Float64`: 無効電力PI制御の比例ゲイン、検証範囲: `(0, nothing)`
  * `K_i::Float64`: 無効電力PI制御の積分ゲイン、検証範囲: `(0, nothing)`
  * `T_ft::Float64`: 無効電力リード時間定数（秒）、検証範囲: `(0, nothing)`
  * `T_fv::Float64`: 無効電力ラグ時間定数（秒）、検証範囲: `(0, nothing)`
  * `V_frz::Float64`: 状態ξq_oc（積分器状態）がフリーズする電圧、検証範囲: `(0, nothing)`
  * `R_c::Float64`: ラインドロップ補償抵抗（VC_Flag = 1のときに使用）、検証範囲: `(0, nothing)`
  * `X_c::Float64`: ラインドロップ補償リアクタンス（VC_Flag = 1のときに使用）、検証範囲: `(0, nothing)`
  * `K_c::Float64`: 無効電流補償ゲイン（pu）（VC_Flag = 0のときに使用）、検証範囲: `(0, nothing)`
  * `e_lim::MinMax`: 電圧またはQ電力デッドバンド出力の上限/下限 `(e_min, e_max)`
  * `dbd_pnts::Tuple{Float64, Float64}`: 電圧またはQ電力エラーのデッドバンド閾値 `(dbd1, dbd2)`
  * `Q_lim::MinMax`: REPCAにおける無効電力V/Q制御の上限/下限 `(Q_min, Q_max)`
  * `T_p::Float64`: REECBにおける有効電力ラグ時間定数（秒）。PF_Flag = 1のときのみ使用、検証範囲: `(0, nothing)`
  * `Q_lim_inner::MinMax`: REECBにおける無効電力入力の上限/下限 `(Q_min_inner, Q_max_inner)`。V_Flag = 1のときのみ使用
  * `V_lim::MinMax`: REECBにおける無効電力PIコントローラーの上限/下限 `(V_min, V_max)`。V_Flag = 1のときのみ使用
  * `K_qp::Float64`: 無効電力レギュレーターの比例ゲイン（V_Flag = 1のときに使用）、検証範囲: `(0, nothing)`
  * `K_qi::Float64`: 無効電力レギュレーターの積分ゲイン（V_Flag = 1のときに使用）、検証範囲: `(0, nothing)`
  * `Q_ref::Float64`: （デフォルト: `1.0`）基準無効電力セットポイント（pu）、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ReactiveRenewableControllerABモデルの[states](@ref S)はフラグに依存します
  * `n_states::Int`: (**変更しないでください。**) ReactiveRenewableControllerABモデルの状態はフラグに依存します
```
