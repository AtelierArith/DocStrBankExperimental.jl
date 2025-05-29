```
contract(a::AlgAssAbsOrdIdl, O::AlgAssAbsOrd) -> AlgAssAbsOrdIdl
intersect(a::AlgAssAbsOrdIdl, O::AlgAssAbsOrd) -> AlgAssAbsOrdIdl
intersect(O::AlgAssAbsOrd, a::AlgAssAbsOrdIdl) -> AlgAssAbsOrdIdl
```

Returns $a \cap O$. It is assumed that the order of $a$ contains $O$.
