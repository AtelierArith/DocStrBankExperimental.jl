```
*(O::AlgAssRelOrd, a::AbsNumFieldOrderIdeal) -> AlgAssRelOrdIdl
*(O::AlgAssRelOrd, a::RelNumFieldOrderIdeal) -> AlgAssRelOrdIdl
*(O::AlgAssRelOrd, a::AbsSimpleNumFieldOrderFractionalIdeal) -> AlgAssRelOrdIdl
*(O::AlgAssRelOrd, a::RelNumFieldOrderFractionalIdeal) -> AlgAssRelOrdIdl
*(a::AbsNumFieldOrderIdeal, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
*(a::RelNumFieldOrderIdeal, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
*(a::AbsSimpleNumFieldOrderFractionalIdeal, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
*(a::RelNumFieldOrderFractionalIdeal, O::AlgAssRelOrd) -> AlgAssRelOrdIdl
```

Returns the ideal $a \cdot O$ where $a$ is a (fractional) ideal of `base_ring(O)`.
