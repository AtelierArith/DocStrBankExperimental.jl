```
restrict_multivector(
    x::AbstractVector{Float64},
    m::Int64,
    qdim::Int64;
    block::Int64 = 1
) -> Vector{Float64}
```

Restricts a multivector of qdim×block×m elements for qdim components  to the regular vector of m blocks of size block.
