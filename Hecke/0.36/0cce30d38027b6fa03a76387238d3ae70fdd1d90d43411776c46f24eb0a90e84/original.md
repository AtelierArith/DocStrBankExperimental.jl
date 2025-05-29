```
ideal(O::AlgAssAbsOrd, x::AbstractAssociativeAlgebraElem, side::Symbol) -> AlgAssAbsOrdIdl
ideal(O::AlgAssAbsOrd, x::AlgAssAbsOrdElem, side::Symbol) -> AlgAssAbsOrdIdl
```

Returns the ideal $O \cdot x$ if `side == :left`, and $x \cdot O$ if `side == :right`.
