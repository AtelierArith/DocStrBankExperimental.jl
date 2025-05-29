```
mutable struct LCFilter <: Filter
    lf::Float64
    rf::Float64
    cf::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

コンバータの外部にあるLCLフィルタのパラメータ

# 引数

  * `lf::Float64`: フィルタインダクタンス、検証範囲: `(0, nothing)`
  * `rf::Float64`: フィルタ抵抗、検証範囲: `(0, nothing)`
  * `cf::Float64`: フィルタキャパシタンス、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) LCFilterモデルの[states](@ref S)は次の通りです:

```
ir_filter: フィルタからの実電流,
ii_filter: フィルタからの虚電流
```

  * `n_states::Int`: (**変更しないでください。**) LCFilterは2つの状態を持ちます。
