```
info_score(b::Bgen, v::BgenVariant; T=Float32, decompressed=nothing)
info_score(p::Preamble, d::Vector{UInt8}, idx::Vector{<:Integer}, layout::UInt8, 
    rmask::Union{Nothing, Vector{UInt16}})
```

バリアントの情報スコア。
