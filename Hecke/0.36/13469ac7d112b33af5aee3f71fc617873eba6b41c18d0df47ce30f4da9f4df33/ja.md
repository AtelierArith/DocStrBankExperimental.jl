```
*(O::AlgAssAbsOrd, x::AbstractAssociativeAlgebraElem) -> AlgAssAbsOrdIdl
*(O::AlgAssAbsOrd, x::AlgAssAbsOrdElem) -> AlgAssAbsOrdIdl
*(O::AlgAssAbsOrd, x::Int) -> AlgAssAbsOrdIdl
*(O::AlgAssAbsOrd, x::ZZRingElem) -> AlgAssAbsOrdIdl
*(x::AbstractAssociativeAlgebraElem, O::AlgAssAbsOrd) -> AlgAssAbsOrdIdl
*(x::AlgAssAbsOrdElem, O::AlgAssAbsOrd) -> AlgAssAbsOrdIdl
*(x::Int, O::AlgAssAbsOrd) -> AlgAssAbsOrdIdl
*(x::ZZRingElem, O::AlgAssAbsOrd) -> AlgAssAbsOrdIdl
```

理想 $O \cdot x$ または $x \cdot O$ をそれぞれ返します。
