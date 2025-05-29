```
mutable struct AverageConverter <: Converter
    rated_voltage::Float64
    rated_current::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

平均コンバータモデルのパラメータ

# 引数

  * `rated_voltage::Float64`: 定格電圧 (V)、検証範囲: `(0, nothing)`
  * `rated_current::Float64`: 定格電流 (A)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度や経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) AverageConverterには[states](@ref S)がありません
  * `n_states::Int`: (**変更しないでください。**) AverageConverterには状態がありません
