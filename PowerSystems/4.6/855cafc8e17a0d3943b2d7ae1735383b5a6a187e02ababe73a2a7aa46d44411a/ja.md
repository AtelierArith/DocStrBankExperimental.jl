```
mutable struct MarconatoMachine <: Machine
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
    T_AA::Float64
    ext::Dict{String, Any}
    γd::Float64
    γq::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

6-[states](@ref S) 同期機械のパラメータ: Marconato モデル

# 引数

  * `R::Float64`: 機械の EMF 後の抵抗（単位）、検証範囲: `(0, nothing)`
  * `Xd::Float64`: d 軸の EMF 後のリアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq::Float64`: q 軸の EMF 後のリアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xd_p::Float64`: d 軸の EMF 後の過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq_p::Float64`: q 軸の EMF 後の過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xd_pp::Float64`: d 軸の EMF 後のサブ過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq_pp::Float64`: q 軸の EMF 後のサブ過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Td0_p::Float64`: 過渡 d 軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_p::Float64`: 過渡 q 軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Td0_pp::Float64`: サブ過渡 d 軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_pp::Float64`: サブ過渡 q 軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `T_AA::Float64`: d 軸の追加漏れの時間定数、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための [*ext*ra 辞書](@ref additional_fields)、例えば緯度と経度。
  * `γd::Float64`: (**変更しないでください。**) 内部方程式
  * `γq::Float64`: (**変更しないでください。**) 内部方程式
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は:

```
ψq: q 軸のステーターフラックス,
ψd: d 軸のステーターフラックス,
eq_p: q 軸の過渡電圧,
ed_p: d 軸の過渡電圧,
eq_pp: q 軸のサブ過渡電圧,
ed_pp: d 軸のサブ過渡電圧
```

  * `n_states::Int`: (**変更しないでください。**) MarconatoMachine は 6 つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照
