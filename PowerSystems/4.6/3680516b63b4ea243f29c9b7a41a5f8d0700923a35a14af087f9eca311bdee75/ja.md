```
mutable struct VirtualInertia <: ActivePowerControl
    Ta::Float64
    kd::Float64
    kω::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

SRFを使用したVSMによるアクティブパワーコントローラの仮想慣性のパラメータ

# 引数

  * `Ta::Float64`: VSM慣性定数、検証範囲: `(0, nothing)`
  * `kd::Float64`: VSM減衰定数、検証範囲: `(0, nothing)`
  * `kω::Float64`: 周波数ドロップゲイン、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) VirtualInertiaモデルの[状態](@ref S)は次のとおりです：

```
θ_oc: 仮想同期発電機モデルの位相角変位
ω_oc: 仮想同期発電機モデルの回転基準フレームの速度
```

  * `n_states::Int`: (**変更しないでください。**) VirtualInertiaは2つの状態を持ちます
