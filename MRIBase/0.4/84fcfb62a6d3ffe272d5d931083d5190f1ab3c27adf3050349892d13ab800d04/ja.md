```
AcquisitionData(tr::K,kdata::Array{Matrix{Complex{T}},3}; seqInfo=Dict{Symbol,Any}()
                    , idx=nothing, encodingSize=Int64[0,0,0], fov=Float64[0,0,0]
                    , kargs...) where {K <: Union{Trajectory,Vector{Trajectory}},T <: AbstractFloat}
```

`AcquisitionData`のコンストラクタ

# 引数

  * `tr <: Union{Trajectory,Vector{Trajectory}}` - 軌道
  * `kdata::Array{Matrix{Complex{<:AbstractFloat}},3}` - k空間データ

`AcquisitionData`の他のフィールドはキーワード引数として渡すことができます。
