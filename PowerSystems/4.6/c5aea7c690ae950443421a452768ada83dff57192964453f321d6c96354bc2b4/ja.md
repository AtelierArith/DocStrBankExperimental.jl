```
mutable struct ActiveRenewableControllerAB <: ActivePowerControl
    bus_control::Int
    from_branch_control::Int
    to_branch_control::Int
    branch_id_control::String
    Freq_Flag::Int
    K_pg::Float64
    K_ig::Float64
    T_p::Float64
    fdbd_pnts::Tuple{Float64, Float64}
    fe_lim::MinMax
    P_lim::MinMax
    T_g::Float64
    D_dn::Float64
    D_up::Float64
    dP_lim::MinMax
    P_lim_inner::MinMax
    T_pord::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

アクティブパワーコントローラーのパラメータ（REPCA1およびREECB1を含む）

# 引数

  * `bus_control::Int`: 電圧制御のためのACBus識別[`number`](@ref ACBus)。`0`はこのコンポーネントに接続されたローカルバスを識別し、検証範囲: `(0, nothing)`
  * `from_branch_control::Int`: ラインドロップ補償のための監視されたブランチFROMバス番号（0の場合は発電機の電力が使用される）、検証範囲: `(0, nothing)`
  * `to_branch_control::Int`: ラインドロップ補償のための監視されたブランチTOバス番号（0の場合は発電機の電力が使用される）、検証範囲: `(0, nothing)`
  * `branch_id_control::String`: ラインドロップ補償のためのブランチ回路ID（文字列として）。0の場合は発電機の電力が使用される
  * `Freq_Flag::Int`: REPCA1の周波数フラグ: 0: 無効、1: 有効、検証範囲: `(0, 1)`
  * `K_pg::Float64`: アクティブパワーPI制御の比例ゲイン、検証範囲: `(0, nothing)`
  * `K_ig::Float64`: アクティブパワーPI制御の積分ゲイン、検証範囲: `(0, nothing)`
  * `T_p::Float64`: 実効電力測定フィルターの時間定数（秒）、検証範囲: `(0, nothing)`
  * `fdbd_pnts::Tuple{Float64, Float64}`: 周波数誤差デッドバンドの閾値 `(fdbd1, fdbd2)`
  * `fe_lim::MinMax`: 周波数誤差の上限/下限 `(fe_min, fe_max)`
  * `P_lim::MinMax`: 電力リファレンスの上限/下限 `(P_min, P_max)`
  * `T_g::Float64`: パワーコントローラーの遅延時間定数、検証範囲: `(0, nothing)`
  * `D_dn::Float64`: 過周波数条件のドロップ、検証範囲: `(nothing, 0)`
  * `D_up::Float64`: 低周波数条件のドロップ、検証範囲: `(0, nothing)`
  * `dP_lim::MinMax`: 電力リファレンスのランプレートの上限/下限 `(dP_min, dP_max)`
  * `P_lim_inner::MinMax`: REECBの電力リファレンスの上限/下限 `(P_min_inner, P_max_inner)`
  * `T_pord::Float64`: REECBのパワーフィルター時間定数、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: （デフォルト: `1.0`）リファレンスパワーセットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ActiveRenewableControllerABモデルの[states](@ref S)はフラグに依存します
  * `n_states::Int`: (**変更しないでください。**) ActiveRenewableControllerABモデルの状態はフラグに依存します
