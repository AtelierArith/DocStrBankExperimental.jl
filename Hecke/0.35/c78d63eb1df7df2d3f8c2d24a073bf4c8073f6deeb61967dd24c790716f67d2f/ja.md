```
*(a::AlgAssAbsOrdIdl, x::Int) -> AlgAssAbsOrdIdl
*(x::Int, a::AlgAssAbsOrdIdl) -> AlgAssAbsOrdIdl
*(a::AlgAssAbsOrdIdl, x::ZZRingElem) -> AlgAssAbsOrdIdl
*(x::ZZRingElem, a::AlgAssAbsOrdIdl) -> AlgAssAbsOrdIdl
*(a::AlgAssAbsOrdIdl, x::QQFieldElem) -> AlgAssAbsOrdIdl
*(x::QQFieldElem, a::AlgAssAbsOrdIdl) -> AlgAssAbsOrdIdl
*(a::AlgAssAbsOrdIdl{S, T}, x::T) where { S, T } -> AlgAssAbsOrdIdl{S, T}
*(x::T, a::AlgAssAbsOrdIdl{S, T}) where { S, T } -> AlgAssAbsOrdIdl{S, T}
*(a::AlgAssAbsOrdIdl{S, T}, x::AlgAssAbsOrdElem{S, T}) where { S, T }
  -> AlgAssAbsOrdIdl{S, T}
*(x::AlgAssAbsOrdElem{S, T}, a::AlgAssAbsOrdIdl{S, T}) where { S, T }
  -> AlgAssAbsOrdIdl{S, T}
```

理想 $a*x$ および $x*a$ をそれぞれ返します。
