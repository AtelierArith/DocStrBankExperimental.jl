```
mutable struct RLFilter <: Filter
    rf::Float64
    lf::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

RL系列フィルタの代数的表現のパラメータ

# 引数

  * `rf::Float64`: グリッドへのコンバータフィルタの系列抵抗（p.u.）、検証範囲: `(0, nothing)`
  * `lf::Float64`: グリッドへのコンバータフィルタの系列インダクタンス（p.u.）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) RLFilterはゼロの[states](@ref S)を持ちます
  * `n_states::Int`: (**変更しないでください。**) RLFilterはゼロの状態を持ちます
