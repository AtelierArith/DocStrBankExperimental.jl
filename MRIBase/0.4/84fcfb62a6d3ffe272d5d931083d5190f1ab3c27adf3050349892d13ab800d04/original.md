```
AcquisitionData(tr::K,kdata::Array{Matrix{Complex{T}},3}; seqInfo=Dict{Symbol,Any}()
                    , idx=nothing, encodingSize=Int64[0,0,0], fov=Float64[0,0,0]
                    , kargs...) where {K <: Union{Trajectory,Vector{Trajectory}},T <: AbstractFloat}
```

constructor for `AcquisitionData`

# Arguments

  * `tr <: Union{Trajectory,Vector{Trajectory}}` - trajectories
  * `kdata::Array{Matrix{Complex{<:AbstractFloat}},3}` - k-space data

the other fields of `AcquisitionData` can be passed as keyword arguments.
