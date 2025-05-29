```
mutable struct ActivePowerDroop <: ActivePowerControl
    Rp::Float64
    ωz::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

アクティブパワードループコントローラのパラメータ

# 引数

  * `Rp::Float64`: ドループゲイン、検証範囲: `(0, nothing)`
  * `ωz::Float64`: フィルタ周波数カットオフ、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照パワーセットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ActivePowerDroopモデルの[states](@ref S)は次の通りです:

```
θ_oc: インバータモデルの位相角変位、
p_oc: インバータモデルの測定されたアクティブパワー
```

  * `n_states::Int`: (**変更しないでください。**) ActivePowerDroopは2つの状態を持ちます。
