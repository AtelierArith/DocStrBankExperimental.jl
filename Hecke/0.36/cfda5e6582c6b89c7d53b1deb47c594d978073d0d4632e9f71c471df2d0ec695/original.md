```
ideal(O::AlgAssRelOrd, x::AbstractAssociativeAlgebraElem, side::Symbol) -> AlgAssRelOrdIdl
ideal(O::AlgAssRelOrd, x::AlgAssRelOrdElem, side::Symbol) -> AlgAssRelOrdIdl
```

Returns the ideal $O \cdot x$ if `side == :left`, and $x \cdot O$ if `side == :right`.
