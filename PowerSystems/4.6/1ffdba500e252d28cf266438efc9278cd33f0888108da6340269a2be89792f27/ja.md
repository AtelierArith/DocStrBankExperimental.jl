```
mutable struct AndersonFouadMachine <: Machine
    R::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xq_p::Float64
    Xd_pp::Float64
    Xq_pp::Float64
    Td0_p::Float64
    Tq0_p::Float64
    Td0_pp::Float64
    Tq0_pp::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

6-[states](@ref S) 同期機械のパラメータ: アンダーソン-ファウドモデル

# 引数

  * `R::Float64`: 機械のEMF後の抵抗（単位）、検証範囲: `(0, nothing)`
  * `Xd::Float64`: d軸のEMF後のリアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq::Float64`: q軸のEMF後のリアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xd_p::Float64`: d軸のEMF後の過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq_p::Float64`: q軸のEMF後の過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xd_pp::Float64`: d軸のEMF後のサブ過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq_pp::Float64`: q軸のEMF後のサブ過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Td0_p::Float64`: 過渡d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_p::Float64`: 過渡q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Td0_pp::Float64`: サブ過渡d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_pp::Float64`: サブ過渡q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は:

```
ψq: q軸のステーターフラックス,
ψd: d軸のステーターフラックス,
eq_p: q軸の過渡電圧,
ed_p: d軸の過渡電圧,
eq_pp: q軸のサブ過渡電圧,
ed_pp: d軸のサブ過渡電圧
```

  * `n_states::Int`: (**変更しないでください。**) AndersonFouadMachineは6つの状態を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
