```
prolong_multivector(
    x::AbstractVector{Float64},
    m::Int64,
    qdim::Int64; 
    block::Int64 = 1
) -> Vector{Float64}
```

Prolongates a vector of m blocks of size block to a multivector  for qdim components of length qdim×block×m.
