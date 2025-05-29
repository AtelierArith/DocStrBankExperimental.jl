```
mutable struct AggregateDistributedGenerationA <: DynamicInjection
    name::String
    Pf_Flag::Int
    Freq_Flag::Int
    PQ_Flag::Int
    Gen_Flag::Int
    Vtrip_Flag::Int
    Ftrip_Flag::Int
    T_rv::Float64
    Trf::Float64
    dbd_pnts::Tuple{Float64, Float64}
    K_qv::Float64
    Tp::Float64
    T_iq::Float64
    D_dn::Float64
    D_up::Float64
    fdbd_pnts::Tuple{Float64, Float64}
    fe_lim::MinMax
    P_lim::MinMax
    dP_lim::MinMax
    Tpord::Float64
    Kpg::Float64
    Kig::Float64
    I_max::Float64
    vl_pnts::Vector{Tuple{Float64,Float64}}
    vh_pnts::Vector{Tuple{Float64,Float64}}
    Vrfrac::Float64
    fl::Float64
    fh::Float64
    tfl::Float64
    tfh::Float64
    Tg::Float64
    rrpwr::Float64
    Tv::Float64
    Vpr::Float64
    Iq_lim::MinMax
    V_ref::Float64
    Pfa_ref::Float64
    ω_ref::Float64
    Q_ref::Float64
    P_ref::Float64
    base_power::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

DERA1モデルのPSS/Eにおけるパラメータ

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例: `PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `Pf_Flag::Int`: 力率制御のフラグ、検証範囲: `(0, 1)`
  * `Freq_Flag::Int`: 周波数制御の有効/無効を設定するフラグ、検証範囲: `(0, 1)`
  * `PQ_Flag::Int`: 最大電流を強制するために使用されるフラグ、検証範囲: `(0, 1)`
  * `Gen_Flag::Int`: 発電機またはストレージを指定するためのフラグ、検証範囲: `(0, 1)`
  * `Vtrip_Flag::Int`: 電圧トリップロジックの有効/無効を設定するフラグ、検証範囲: `(0, 1)`
  * `Ftrip_Flag::Int`: 周波数トリップロジックの有効/無効を設定するフラグ、検証範囲: `(0, 1)`
  * `T_rv::Float64`: 電圧測定トランスデューサの時間定数、検証範囲: `(0, nothing)`
  * `Trf::Float64`: 周波数測定トランスデューサの時間定数、検証範囲: `(0, nothing)`
  * `dbd_pnts::Tuple{Float64, Float64}`: 電圧デッドバンドの閾値 `(dbd1, dbd2)`
  * `K_qv::Float64`: 比例電圧制御ゲイン (pu)、検証範囲: `(0, nothing)`
  * `Tp::Float64`: 電力測定トランスデューサの時間定数、検証範囲: `(0, nothing)`
  * `T_iq::Float64`: QFlag = 0のときの状態q_Vのためのローパスフィルタの時間定数、検証範囲: `(0, nothing)`
  * `D_dn::Float64`: 過周波数条件のためのドロップの逆数 (>0) (pu)、検証範囲: `(0, nothing)`
  * `D_up::Float64`: 低周波数条件のためのドロップの逆数 (<=0) (pu)、検証範囲: `(0, nothing)`
  * `fdbd_pnts::Tuple{Float64, Float64}`: 周波数制御デッドバンドの閾値 `(fdbd1, fdbd2)`
  * `fe_lim::MinMax`: 周波数誤差の制限 (femin, femax)
  * `P_lim::MinMax`: 電力の制限 (Pmin, Pmax)
  * `dP_lim::MinMax`: 電力参照のランプレート制限 (dPmin, dPmax)
  * `Tpord::Float64`: 電力フィルタの時間定数、検証範囲: `(0, nothing)`
  * `Kpg::Float64`: PIコントローラの比例ゲイン (pu)、検証範囲: `(0, nothing)`
  * `Kig::Float64`: PIコントローラの積分ゲイン (pu)、検証範囲: `(0, nothing)`
  * `I_max::Float64`: 総コンバータ電流の最大制限 (pu)、検証範囲: `(0, nothing)`
  * `vl_pnts::Vector{Tuple{Float64,Float64}}`: 低電圧カットアウトポイント `[(tv10, vl0), (tv11, vl1)]`
  * `vh_pnts::Vector{Tuple{Float64,Float64}}`: 高電圧カットアウトポイント `[(tvh0, vh0), (tvh1, vh1)]`
  * `Vrfrac::Float64`: 電圧がvl1 < V < vh1に戻った後に回復するデバイスの割合 (0 <= Vrfrac <= 1)、検証範囲: `(0, 1)`
  * `fl::Float64`: 低周波数カットアウトのためのインバータ周波数のブレークポイント (Hz)、検証範囲: `(0, nothing)`
  * `fh::Float64`: 高周波数カットアウトのためのインバータ周波数のブレークポイント (Hz)、検証範囲: `(0, nothing)`
  * `tfl::Float64`: 周波数flに対応する低周波数カットアウトタイマー (s)、検証範囲: `(0, nothing)`
  * `tfh::Float64`: 周波数fhに対応する高周波数カットアウトタイマー (s)、検証範囲: `(0, nothing)`
  * `Tg::Float64`: 現在制御の時間定数 (内部制御ループの動作を表すため) (> 0) (s)、検証範囲: `(0, nothing)`
  * `rrpwr::Float64`: 故障後の実電力増加のランプレート (pu/s)、検証範囲: `(0, nothing)`
  * `Tv::Float64`: 乗算器の出力の時間定数 (s)、検証範囲: `(0, nothing)`
  * `Vpr::Float64`: 周波数トリッピングが無効になる電圧 (pu)、検証範囲: `(0, nothing)`
  * `Iq_lim::MinMax`: 無効電流注入の制限 (Iqll, Iqhl)
  * `V_ref::Float64`: (デフォルト: `1.0`) ユーザー定義の電圧参照。0の場合、[`PowerSimulationsDynamics.jl`](https://nrel-sienna.github.io/PowerSimulationsDynamics.jl/stable/)は初期端子電圧に初期化されます、検証範囲: `(0, nothing)`
  * `Pfa_ref::Float64`: (デフォルト: `0.0`) 参照力率、検証範囲: `(0, nothing)`
  * `ω_ref::Float64`: (デフォルト: `1.0`) 参照周波数 (pu)、検証範囲: `(0, nothing)`
  * `Q_ref::Float64`: (デフォルト: `0.0`) 参照無効電力、pu単位、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照有効電力、pu単位、検証範囲: `(0, nothing)`
  * `base_power::Float64`: (デフォルト: `100.0`) [単位化](@ref per_unit)のための基準電力 (MVA)
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例: 緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) AggregateDistributedGenerationAの[状態](@ref S)はフラグに依存します。
  * `n_states::Int`: (**変更しないでください。**) AggregateDistributedGenerationAの状態はフラグに依存します。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jlの内部参照
