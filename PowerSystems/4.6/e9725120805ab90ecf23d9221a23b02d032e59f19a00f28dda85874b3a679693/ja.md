```
mutable struct FullMachine <: Machine
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

ゼロ成分フラックスを持たないフルオーダーフラックススタトルーターモデルのパラメータ。スタトルフラックス（ψdおよびψq）の導関数は無視されません。1つのq軸ダンピング回路のみが考慮されています。すべてのパラメータは機械のパー・ユニットです。詳細については、[Power System Stability and Control by P. Kundur](https://www.accessengineeringlibrary.com/content/book/9781260473544)の第3章または[Power System Dynamics: Stability and Control, by J. Machowski, J. Bialek and J. Bumby](https://www.wiley.com/en-us/Power+System+Dynamics%3A+Stability+and+Control%2C+3rd+Edition-p-9781119526360)の第11章を参照してください。両方の書籍で使用される異なるパーク変換のため、モデルは若干異なりますが（しかし同等です）。

# 引数

  * `R::Float64`: 機械のEMF後の抵抗、パー・ユニット、検証範囲: `(0, nothing)`
  * `R_f::Float64`: パー・ユニットのフィールドロータ巻線抵抗、検証範囲: `(0, nothing)`
  * `R_1d::Float64`: d軸のダンピングロータ巻線抵抗、パー・ユニット。この値はMachowskiでRDと表記されます、検証範囲: `(0, nothing)`
  * `R_1q::Float64`: q軸のダンピングロータ巻線抵抗、パー・ユニット。この値はMachowskiでRQと表記されます、検証範囲: `(0, nothing)`
  * `L_d::Float64`: ロータのd軸における三相スタトル巻線の影響を表す架空のダンピングのインダクタンス、パー・ユニット。この値はKundurでL*ad + L*l、MachowskiでLdと表記されます、検証範囲: `(0, nothing)`
  * `L_q::Float64`: ロータのq軸における三相スタトル巻線の影響を表す架空のダンピングのインダクタンス、パー・ユニット。この値はKundurでL*aq + L*lと表記されます、検証範囲: `(0, nothing)`
  * `L_ad::Float64`: スタトル巻線とロータフィールド（およびダンピング）巻線のd軸における相互インダクタンス、パー・ユニット、検証範囲: `(0, nothing)`
  * `L_aq::Float64`: スタトル巻線とロータダンピング巻線のq軸における相互インダクタンス、パー・ユニット、検証範囲: `(0, nothing)`
  * `L_f1d::Float64`: ロータフィールド巻線とロータダンピング巻線のd軸における相互インダクタンス、パー・ユニット、検証範囲: `(0, nothing)`
  * `L_ff::Float64`: フィールドロータ巻線のインダクタンス、パー・ユニット、検証範囲: `(0, nothing)`
  * `L_1d::Float64`: d軸ロータダンピング回路のインダクタンス、パー・ユニット、検証範囲: `(0, nothing)`
  * `L_1q::Float64`: q軸ロータダンピング回路のインダクタンス、パー・ユニット、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `inv_d_fluxlink::Array{Float64,2}`: (**変更しないでください。**) Kundurからの式3.127、3.130、3.131
  * `inv_q_fluxlink::Array{Float64,2}`: (**変更しないでください。**) Kundurからの式3.128、3.132
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S)は次の通りです：

```
ψd: d軸スタトルフラックス、
ψq: q軸スタトルフラックス、
ψf: フィールドロータフラックス、
ψ1d: d軸ロータダンピングフラックス、
ψ1q: q軸ロータダンピングフラックス
```

  * `n_states::Int`: (**変更しないでください。**) FullMachineは5つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
