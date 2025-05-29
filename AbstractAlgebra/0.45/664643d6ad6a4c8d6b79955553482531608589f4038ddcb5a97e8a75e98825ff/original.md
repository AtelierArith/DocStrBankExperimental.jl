```
crt_with_lcm(r::Vector{T}, m::Vector{T}; check::Bool=true) where T <: RingElement
```

Return a tuple consisting of an element congruent to $r_i$ modulo $m_i$ for each $i$ and the least common multiple of the $m_i$.
