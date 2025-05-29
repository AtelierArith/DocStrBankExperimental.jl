```
mutable struct RECurrentControlB <: InnerControl
    Q_Flag::Int
    PQ_Flag::Int
    Vdip_lim::MinMax
    T_rv::Float64
    dbd_pnts::Tuple{Float64, Float64}
    K_qv::Float64
    Iqinj_lim::MinMax
    V_ref0::Float64
    K_vp::Float64
    K_vi::Float64
    T_iq::Float64
    I_max::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

PSS/EにおけるREECBモデルの内部制御部分のパラメータ

# 引数

  * `Q_Flag::Int`: I_qinjに使用されるQフラグ、検証範囲: `(0, 1)`
  * `PQ_Flag::Int`: 現在制限ロジックに使用されるPQフラグ、検証範囲: `(0, 1)`
  * `Vdip_lim::MinMax`: 電圧ディップロジックの制限 `(Vdip, Vup)`
  * `T_rv::Float64`: 電圧フィルターの時間定数、検証範囲: `(0, nothing)`
  * `dbd_pnts::Tuple{Float64, Float64}`: 電圧誤差デッドバンドの閾値 `(dbd1, dbd2)`
  * `K_qv::Float64`: 過電圧および低電圧条件下での無効電流注入ゲイン、検証範囲: `(0, nothing)`
  * `Iqinj_lim::MinMax`: Iqinjの制限 `(I_qh1, I_ql1)`
  * `V_ref0::Float64`: ユーザー定義の基準。0の場合、[`PowerSimulationsDynamics.jl`](https://nrel-sienna.github.io/PowerSimulationsDynamics.jl/stable/)は初期端子電圧に初期化され、検証範囲: `(0, nothing)`
  * `K_vp::Float64`: 電圧レギュレータの比例ゲイン（QFlag = 1のときに使用）、検証範囲: `(0, nothing)`
  * `K_vi::Float64`: 電圧レギュレータの積分ゲイン（QFlag = 1のときに使用）、検証範囲: `(0, nothing)`
  * `T_iq::Float64`: QFlag = 0のときの状態q_Vのためのローパスフィルターの時間定数、検証範囲: `(0, nothing)`
  * `I_max::Float64`: 総コンバータ電流の最大制限、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) RECurrentControlBの[states](@ref S)はフラグに依存します
  * `n_states::Int`: (**変更しないでください。**) RECurrentControlBの状態はフラグに依存します
