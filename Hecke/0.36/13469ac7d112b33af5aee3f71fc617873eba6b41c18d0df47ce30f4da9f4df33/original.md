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

Returns the ideal $O \cdot x$ or $x \cdot O$ respectively.
