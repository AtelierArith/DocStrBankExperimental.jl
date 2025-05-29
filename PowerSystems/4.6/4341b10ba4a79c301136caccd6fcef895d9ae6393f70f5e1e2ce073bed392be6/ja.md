```
mutable struct OneDOneQMachine <: Machine
    R::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xq_p::Float64
    Td0_p::Float64
    Tq0_p::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

4-[states](@ref S) 同期機械のパラメータ: 簡略化されたマルコナートモデル ステーターフラックス (ψd と ψq) の導関数は無視され、ωψd = ψd および ωψq = ψq が仮定されます (すなわち、ω=1.0)。これは、送電網の動力学が無視される場合の標準です。

# 引数

  * `R::Float64`: 機械のEMF後の抵抗（単位あたり）、検証範囲: `(0, nothing)`
  * `Xd::Float64`: d軸のEMF後のリアクタンス（単位あたり）、検証範囲: `(0, nothing)`
  * `Xq::Float64`: q軸のEMF後のリアクタンス（単位あたり）、検証範囲: `(0, nothing)`
  * `Xd_p::Float64`: d軸のEMF後の過渡リアクタンス（単位あたり）、検証範囲: `(0, nothing)`
  * `Xq_p::Float64`: q軸のEMF後の過渡リアクタンス（単位あたり）、検証範囲: `(0, nothing)`
  * `Td0_p::Float64`: 過渡d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_p::Float64`: 過渡q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は:

```
eq_p: q軸過渡電圧,
ed_p: d軸過渡電圧
```

  * `n_states::Int`: (**変更しないでください。**) OneDOneQMachine は 2 つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照
