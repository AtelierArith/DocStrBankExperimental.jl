```
ideal(O::AlgAssRelOrd, x::AbstractAssociativeAlgebraElem, side::Symbol) -> AlgAssRelOrdIdl
ideal(O::AlgAssRelOrd, x::AlgAssRelOrdElem, side::Symbol) -> AlgAssRelOrdIdl
```

`side`が`:left`の場合は理想$O \cdot x$を返し、`:right`の場合は$x \cdot O$を返します。
