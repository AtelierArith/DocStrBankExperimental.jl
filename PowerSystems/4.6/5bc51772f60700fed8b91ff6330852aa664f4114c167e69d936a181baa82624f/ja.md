```
mutable struct CurrentModeControl <: InnerControl
    kpc::Float64
    kic::Float64
    kffv::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

["並列接続された三相グリッド接続インバータのための縮小次数構造保存モデル"](https://doi.org/10.1109/COMPEL.2017.8013389)に基づく内部ループ比例積分（PI）電流制御のパラメータ

# 引数

  * `kpc::Float64`: 電流制御器の比例ゲイン、検証範囲: `(0, nothing)`
  * `kic::Float64`: 電流制御器の積分ゲイン、検証範囲: `(0, nothing)`
  * `kffv::Float64`: 電圧のフィードフォワードゲインを有効にするためのゲイン、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) CurrentModeControlモデルの[状態](@ref S)は次の通りです：

```
γd_ic: PI電流制御器のd軸積分器状態、
γq_ic: PI電流制御器のq軸積分器状態
```

  * `n_states::Int`: (**変更しないでください。**) CurrentControlは2つの状態を持ちます
