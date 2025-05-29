```
hwe(b::Bgen, v::BgenVariant; T=Float32, decompressed=nothing)
hwe(p::Preamble, d::Vector{UInt8}, idx::Vector{<:Integer}, layout::UInt8, 
    rmask::Union{Nothing, Vector{UInt16}})
```

二倍体二対立遺伝子の場合のハーディー・ワインバーグ平衡検定
