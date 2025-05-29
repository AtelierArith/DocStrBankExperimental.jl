```
mutable struct DEGOV1 <: TurbineGov
    droop_flag::Int
    T1::Float64
    T2::Float64
    T3::Float64
    K::Float64
    T4::Float64
    T5::Float64
    T6::Float64
    Td::Float64
    T_lim::Tuple{Float64, Float64}
    R::Float64
    Te::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

ウッドワードディーゼルガバナーモデルのパラメータ。PSSEのDEGOV1

# 引数

  * `droop_flag::Int`: ドループ制御フラグ。スロットルフィードバックの場合は0、電力フィードバックの場合は1、検証範囲: `(0, 1)`
  * `T1::Float64`: ガバナー機構の時間定数（秒）、検証範囲: `(0, 100)`
  * `T2::Float64`: タービン出力の時間定数（秒）、検証範囲: `(0, 100)`
  * `T3::Float64`: タービン排気温度の時間定数（秒）、検証範囲: `(0, 100)`
  * `K::Float64`: アクチュエーター用のガバナーゲイン、検証範囲: `(0, 100)`
  * `T4::Float64`: ガバナーリード時間定数（秒）、検証範囲: `(0, 100)`
  * `T5::Float64`: ガバナーラグ時間定数（秒）、検証範囲: `(0, 100)`
  * `T6::Float64`: アクチュエーターの時間定数（秒）、検証範囲: `(0, 100)`
  * `Td::Float64`: エンジンの時間遅延（秒）、検証範囲: `(0, 100)`
  * `T_lim::Tuple{Float64, Float64}`: アクチュエーターの運用制御限界（T*min, T*max）
  * `R::Float64`: 定常状態のドループパラメータ、検証範囲: `(0, 100)`
  * `Te::Float64`: 電力トランスデューサの時間定数（秒）、検証範囲: `(0, 100)`
  * `P_ref::Float64`: （デフォルト: `1.0`）参照負荷セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) DEGOV1モデルの[states](@ref S)はドループフラグに依存します
  * `n_states::Int`: (**変更しないでください。**) DEGOV1モデルの[states](@ref S)の数はドループフラグに依存します
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
