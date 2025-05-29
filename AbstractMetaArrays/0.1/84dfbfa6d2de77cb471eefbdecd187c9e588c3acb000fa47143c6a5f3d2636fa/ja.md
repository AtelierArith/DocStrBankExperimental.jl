```
SimpleMetaArray{T,N}(data::A, metadata::DictOrNothing=nothing, colmetadata::Union{NTuple{N,DictOrNothing},DictOrNothing}=nothing) where {T,N,A<:AbstractArray{T,N}} =
SimpleMetaArray(data, metadata, colmetadata)
```

与えられたデータ、メタデータ、および列メタデータを使用して `SimpleMetaArray` を構築します。

# 例

```jldocs
julia> using StaticArrays
julia> s=SimpleMetaArray(SVector{3}(1,1,1), Dict("description" => ("test array", :entry)),
              Dict("unit" => ("m", :default)))
3-element SimpleMetaArray{Int64, 1} with indices SOneTo(3):
 1
 1
 1

julia> metadata(s)
Dict{String, String} with 1 entry:
  "description" => "test array"

julia> colmetadata(s)
Dict{Symbol, Dict{String, String}} with 3 entries:
  :y => Dict("unit"=>"m")
  :z => Dict("unit"=>"m")
  :x => Dict("unit"=>"m")
```
