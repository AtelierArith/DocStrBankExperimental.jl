```
mutable struct GenericDER <: DynamicInjection
    name::String
    Qref_Flag::Int
    PQ_Flag::Int
    Gen_Flag::Int
    PerOp_Flag::Int
    Recon_Flag::Int
    Trv::Float64
    VV_pnts::NamedTuple{(:V1, :V2, :V3, :V4), Tuple{Float64, Float64, Float64, Float64}}
    Q_lim::MinMax
    Tp::Float64
    e_lim::MinMax
    Kpq::Float64
    Kiq::Float64
    Iqr_lim::MinMax
    I_max::Float64
    Tg::Float64
    kWh_Cap::Float64
    SOC_ini::Float64
    SOC_lim::MinMax
    Trf::Float64
    fdbd_pnts::NamedTuple{(:fdbd1, :fdbd2), Tuple{Float64, Float64}}
    D_dn::Float64
    D_up::Float64
    fe_lim::MinMax
    Kpp::Float64
    Kip::Float64
    P_lim::MinMax
    dP_lim::MinMax
    T_pord::Float64
    rrpwr::Float64
    VRT_pnts::NamedTuple{(:vrt1, :vrt2, :vrt3, :vrt4, :vrt5), Tuple{Float64, Float64, Float64, Float64, Float64}}
    TVRT_pnts::NamedTuple{(:tvrt1, :tvrt2, :tvrt3), Tuple{Float64, Float64, Float64}}
    tV_delay::Float64
    VES_lim::MinMax
    FRT_pnts::NamedTuple{(:frt1, :frt2, :frt3, :frt4), Tuple{Float64, Float64, Float64, Float64}}
    TFRT_pnts::NamedTuple{(:tfrt1, :tfrt2), Tuple{Float64, Float64}}
    tF_delay::Float64
    FES_lim::MinMax
    Pfa_ref::Float64
    Q_ref::Float64
    P_ref::Float64
    base_power::Float64
    states::Vector{Symbol}
    n_states::Int
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

Generic Distributed Energy Resourceモデルのパラメータ。["モデル化フレームワークとDERおよび柔軟な負荷の調整による補助サービスの提供。"](http://hdl.handle.net/10125/70994)に基づく

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `Qref_Flag::Int`: 無効化電力制御モード。1はVoltVar制御、2は定常Q制御、3は定常PF制御、検証範囲: `(1, 3)`
  * `PQ_Flag::Int`: 有効電力と無効電力の優先モード。Q優先の場合は0、P優先の場合は1、検証範囲: `(0, 1)`
  * `Gen_Flag::Int`: 発電機または蓄電システムを定義します。0は蓄電装置、1は発電機、検証範囲: `(0, 1)`
  * `PerOp_Flag::Int`: VRT特性における許可された領域の操作を定義します。停止の場合は0、連続運転の場合は1、検証範囲: `(0, 1)`
  * `Recon_Flag::Int`: DERが電圧ライドスルー切断後に再接続できるかどうかを定義します。検証範囲: `(0, 1)`
  * `Trv::Float64`: 電圧測定トランスデューサの時間定数、単位は秒、検証範囲: `(0, nothing)`
  * `VV_pnts::NamedTuple{(:V1, :V2, :V3, :V4), Tuple{Float64, Float64, Float64, Float64}}`: Y軸Volt-var曲線のポイント（V1,V2,V3,V4）
  * `Q_lim::MinMax`: 無効電力の制限（pu）（Q*min, Q*max）
  * `Tp::Float64`: 電力測定トランスデューサの時間定数、単位は秒、検証範囲: `(0, nothing)`
  * `e_lim::MinMax`: q制御のPIコントローラの誤差限界（e*min, e*max）
  * `Kpq::Float64`: q制御のPIコントローラの比例ゲイン、検証範囲: `(0, nothing)`
  * `Kiq::Float64`: q制御のPIコントローラの積分ゲイン、検証範囲: `(0, nothing)`
  * `Iqr_lim::MinMax`: 無効電流の変化率の制限（pu/s）（Iqr*min, Iqr*max）
  * `I_max::Float64`: 最大インバータ電流、検証範囲: `(0, nothing)`
  * `Tg::Float64`: 電流制御の時間定数、単位は秒、検証範囲: `(0, nothing)`
  * `kWh_Cap::Float64`: BESSの容量（kWh）、検証範囲: `(0, nothing)`
  * `SOC_ini::Float64`: 初期充電状態（SOC）、pu単位、検証範囲: `(0, 1)`
  * `SOC_lim::MinMax`: バッテリーのSOC制限（SOC*min, SOC*max）
  * `Trf::Float64`: システム周波数を推定するための時間定数、単位は秒、検証範囲: `(0, nothing)`
  * `fdbd_pnts::NamedTuple{(:fdbd1, :fdbd2), Tuple{Float64, Float64}}`: 周波数誤差デッドバンドの閾値（fdbd1, fdbd2）
  * `D_dn::Float64`: 過周波数条件のためのドロップの逆数、pu単位、検証範囲: `(0, nothing)`
  * `D_up::Float64`: 不足周波数条件のためのドロップの逆数、pu単位、検証範囲: `(0, nothing)`
  * `fe_lim::MinMax`: 周波数誤差の制限（pu）（fe*min, fe*max）
  * `Kpp::Float64`: p制御のPIコントローラの比例ゲイン、検証範囲: `(0, nothing)`
  * `Kip::Float64`: p制御のPIコントローラの積分ゲイン、検証範囲: `(0, nothing)`
  * `P_lim::MinMax`: 有効電力の制限（pu）（P*min, P*max）
  * `dP_lim::MinMax`: 有効電力のランプレート制限（pu/s）（dP*min, dP*max）
  * `T_pord::Float64`: 電力フィルタの時間定数、単位は秒、検証範囲: `(0, nothing)`
  * `rrpwr::Float64`: 故障後の実電力増加のランプレート、pu/s単位、検証範囲: `(0, nothing)`
  * `VRT_pnts::NamedTuple{(:vrt1, :vrt2, :vrt3, :vrt4, :vrt5), Tuple{Float64, Float64, Float64, Float64, Float64}}`: 電圧ライドスルーのvポイント（vrt1,vrt2,vrt3,vrt4,vrt5）
  * `TVRT_pnts::NamedTuple{(:tvrt1, :tvrt2, :tvrt3), Tuple{Float64, Float64, Float64}}`: 電圧ライドスルーの時間ポイント（tvrt1,tvrt2,tvrt3）
  * `tV_delay::Float64`: 電圧ライドスルー切断後の再接続のための時間遅延、検証範囲: `(0, nothing)`
  * `VES_lim::MinMax`: サービス開始のための最小および最大電圧（VES*min,VES*max）
  * `FRT_pnts::NamedTuple{(:frt1, :frt2, :frt3, :frt4), Tuple{Float64, Float64, Float64, Float64}}`: 周波数ライドスルーのvポイント（frt1,frt2,frt3,frt4）
  * `TFRT_pnts::NamedTuple{(:tfrt1, :tfrt2), Tuple{Float64, Float64}}`: 周波数ライドスルーの時間ポイント（tfrt1,tfrt2）
  * `tF_delay::Float64`: 周波数ライドスルー切断後の再接続のための時間遅延、検証範囲: `(0, nothing)`
  * `FES_lim::MinMax`: サービス開始のための最小および最大周波数（FES*min,FES*max）
  * `Pfa_ref::Float64`: （デフォルト: `0.0`）基準力率、検証範囲: `(0, nothing)`
  * `Q_ref::Float64`: （デフォルト: `0.0`）基準無効電力、pu単位、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: （デフォルト: `1.0`）基準有効電力、pu単位、検証範囲: `(0, nothing)`
  * `base_power::Float64`: （デフォルト: `100.0`）単位の基準電力（MVA）[パー・ユニット化](@ref per_unit)のため
  * `states::Vector{Symbol}`: (**変更しないでください。**) GenericDERの[状態](@ref S)はフラグに依存します
  * `n_states::Int`: (**変更しないでください。**) GenericDERの[状態](@ref S)はフラグに依存します
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
