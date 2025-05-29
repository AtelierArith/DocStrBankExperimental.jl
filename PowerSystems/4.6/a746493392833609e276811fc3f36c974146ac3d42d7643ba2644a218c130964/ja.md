```
mutable struct LCLFilter <: Filter
    lf::Float64
    rf::Float64
    cf::Float64
    lg::Float64
    rg::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

コンバータの外部にあるLCLフィルタのパラメータ、[states](@ref S)はグリッドの参照フレームにあります

# 引数

  * `lf::Float64`: コンバータフィルタのp.u.における直列インダクタンス、検証範囲: `(0, nothing)`
  * `rf::Float64`: コンバータフィルタのp.u.における直列抵抗、検証範囲: `(0, nothing)`
  * `cf::Float64`: コンバータフィルタのp.u.におけるシャントキャパシタンス、検証範囲: `(0, nothing)`
  * `lg::Float64`: グリッドに対するコンバータフィルタのp.u.における直列インダクタンス、検証範囲: `(0, nothing)`
  * `rg::Float64`: グリッドに対するコンバータフィルタのp.u.における直列抵抗、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) LCLFilterモデルの[states](@ref S)は次の通りです：

```
ir_cnv: コンバータからの実電流、
ii_cnv: コンバータからの虚電流、
vr_filter: フィルタのキャパシタでの実電圧、
vi_filter: フィルタのキャパシタでの虚電圧、
ir_filter: フィルタからの実電流、
ii_filter: フィルタからの虚電流
```

  * `n_states::Int`: (**変更しないでください。**) LCLFilterは6つの状態を持っています
