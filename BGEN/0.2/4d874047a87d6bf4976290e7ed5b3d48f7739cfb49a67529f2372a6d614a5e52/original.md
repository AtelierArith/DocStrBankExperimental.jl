```
hwe(b::Bgen, v::BgenVariant; T=Float32, decompressed=nothing)
hwe(p::Preamble, d::Vector{UInt8}, idx::Vector{<:Integer}, layout::UInt8, 
    rmask::Union{Nothing, Vector{UInt16}})
```

Hardy-Weinberg equilibrium test for diploid biallelic case
