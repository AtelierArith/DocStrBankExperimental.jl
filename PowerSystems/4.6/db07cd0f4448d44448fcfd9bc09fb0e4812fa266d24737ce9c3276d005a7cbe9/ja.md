```
mutable struct SimpleFullMachine <: Machine
    R::Float64
    R_f::Float64
    R_1d::Float64
    R_1q::Float64
    L_d::Float64
    L_q::Float64
    L_ad::Float64
    L_aq::Float64
    L_f1d::Float64
    L_ff::Float64
    L_1d::Float64
    L_1q::Float64
    ext::Dict{String, Any}
    inv_d_fluxlink::Array{Float64,2}
    inv_q_fluxlink::Array{Float64,2}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

ゼロシーケンスフラックスを持たないフルオーダーフラックススタター-ローターモデルのパラメータ。 スターターフラックス（ψdおよびψq）の導関数は無視されます。 これは、送電ネットワークのダイナミクスが無視されるときの標準です。 q軸のダンピング回路のみが考慮されています。 すべてのパー単位は機械のパー単位です。 詳細については、P. Kundurの「Power System Stability and Control」の第3章またはJ. Machowski、J. Bialek、J. Bumbyの「Power System Dynamics: Stability and Control」の第11章を参照してください。 両方の本で使用される異なるパーク変換のため、モデルは若干異なります（ただし同等です）。

# 引数

  * `R::Float64`: 機械のEMF後の抵抗、パー単位、検証範囲: `(0, nothing)`
  * `R_f::Float64`: パー単位のフィールドローターワインディング抵抗、検証範囲: `(0, nothing)`
  * `R_1d::Float64`: d軸のパー単位のダンピングローターワインディング抵抗。この値はMachowskiでRDと表されます、検証範囲: `(0, nothing)`
  * `R_1q::Float64`: q軸のパー単位のダンピングローターワインディング抵抗。この値はMachowskiでRQと表されます、検証範囲: `(0, nothing)`
  * `L_d::Float64`: ローターのd軸における三相スターターワインディングの効果を表す架空のダンピングのインダクタンス、パー単位。この値はKundurでL*ad + L*l（MachowskiではLd）と表されます、検証範囲: `(0, nothing)`
  * `L_q::Float64`: ローターのq軸における三相スターターワインディングの効果を表す架空のダンピングのインダクタンス、パー単位。この値はKundurでL*aq + L*lと表されます、検証範囲: `(0, nothing)`
  * `L_ad::Float64`: d軸のスターターワインディングとローターフィールド（およびダンピング）ワインディングインダクタンス間の相互インダクタンス、パー単位、検証範囲: `(0, nothing)`
  * `L_aq::Float64`: q軸のスターターワインディングとローターダンピングワインディングインダクタンス間の相互インダクタンス、パー単位、検証範囲: `(0, nothing)`
  * `L_f1d::Float64`: d軸のローターフィールドワインディングとローターダンピングワインディングインダクタンス間の相互インダクタンス、パー単位、検証範囲: `(0, nothing)`
  * `L_ff::Float64`: フィールドローターワインディングのインダクタンス、パー単位、検証範囲: `(0, nothing)`
  * `L_1d::Float64`: d軸ローターダンピング回路のインダクタンス、パー単位、検証範囲: `(0, nothing)`
  * `L_1q::Float64`: q軸ローターダンピング回路のインダクタンス、パー単位、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `inv_d_fluxlink::Array{Float64,2}`: (**変更しないでください。**) Kundurからの式3.127、3.130、3.131
  * `inv_q_fluxlink::Array{Float64,2}`: (**変更しないでください。**) Kundurからの式3.128、3.132
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S)は：

```
ψf: フィールドローターフラックス、
ψ1d: d軸ローターダンピングフラックス、
ψ1q: q軸ローターダンピングフラックス
```

  * `n_states::Int`: (**変更しないでください。**) SimpleFullMachineは3つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
