```
restrict_multivector(
    x::AbstractVector{Float64},
    m::Int64,
    qdim::Int64;
    block::Int64 = 1
) -> Vector{Float64}
```

qdim成分のために、qdim×block×m要素の多重ベクトルを、サイズblockのmブロックの通常のベクトルに制限します。
