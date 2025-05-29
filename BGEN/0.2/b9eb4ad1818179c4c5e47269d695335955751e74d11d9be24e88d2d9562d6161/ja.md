```
maf(b::Bgen, v::BgenVariant; T=Float32, decompressed=nothing)
maf(p::Preamble, d::Vector{UInt8}, idx::Vector{<:Integer}, layout::UInt8, 
    rmask::Union{Nothing, Vector{UInt16}})
```

二倍体二塩基型の場合のマイナーアレル頻度
