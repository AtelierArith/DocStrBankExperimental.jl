```
prolong_multivector(
    x::AbstractVector{Float64},
    m::Int64,
    qdim::Int64; 
    block::Int64 = 1
) -> Vector{Float64}
```

mブロックのサイズblockのベクトルを、長さqdim×block×mのqdim成分の多重ベクトルに拡張します。
