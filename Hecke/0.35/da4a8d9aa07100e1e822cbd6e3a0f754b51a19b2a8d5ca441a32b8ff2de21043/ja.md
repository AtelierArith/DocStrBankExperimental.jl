```
*(O::AlgAssRelOrd, x::AbstractAssociativeAlgebraElem) -> AlgAssRelOrdIdl
*(O::AlgAssRelOrd, x::AlgAssRelOrdElem) -> AlgAssRelOrdIdl
*(O::AlgAssRelOrd, x::Int) -> AlgAssRelOrdIdl
*(O::AlgAssRelOrd, x::ZZRingElem) -> AlgAssRelOrdIdl
*(x::AbstractAssociativeAlgebraElem, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
*(x::AlgAssRelOrdElem, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
*(x::Int, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
*(x::ZZRingElem, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
```

理想 $O \cdot x$ または $x \cdot O$ をそれぞれ返します。
