```
ideal(O::AlgAssAbsOrd, x::AbstractAssociativeAlgebraElem, side::Symbol) -> AlgAssAbsOrdIdl
ideal(O::AlgAssAbsOrd, x::AlgAssAbsOrdElem, side::Symbol) -> AlgAssAbsOrdIdl
```

`side == :left` の場合は理想 $O \cdot x$ を返し、`side == :right` の場合は $x \cdot O$ を返します。
