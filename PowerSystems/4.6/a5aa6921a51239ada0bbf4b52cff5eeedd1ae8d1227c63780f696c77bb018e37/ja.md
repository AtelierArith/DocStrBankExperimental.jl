```
mutable struct FixedFrequency <: FrequencyEstimator
    frequency::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

固定周波数推定器のパラメータ（すなわち、PLLなし）

# 引数

  * `frequency::Float64`: (デフォルト: `1.0`) 参照周波数 (pu)
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) FixedFrequencyには[状態](@ref S)がありません
  * `n_states::Int`: (**変更しないでください。**) FixedFrequencyには状態がありません
