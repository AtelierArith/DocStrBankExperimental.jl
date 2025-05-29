```
mutable struct ReactivePowerDroop <: ReactivePowerControl
    kq::Float64
    ωf::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

リアクティブパワードループコントローラのパラメータ

# 引数

  * `kq::Float64`: 周波数ドロップゲイン、検証範囲: `(0, nothing)`
  * `ωf::Float64`: フィルタ周波数カットオフ、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) リアクティブパワードループモデルの[状態](@ref S)は次のとおりです:

```
q_oc: フィルタされたリアクティブ出力電力
```

  * `n_states::Int`: (**変更しないでください。**) ReactivePowerDroopは1つの状態を持ちます
