```
crt_with_lcm(r::Vector{T}, m::Vector{T}; check::Bool=true) where T <: RingElement
```

各 $i$ に対して $m_i$ で $r_i$ と合同な要素と $m_i$ の最小公倍数からなるタプルを返します。
