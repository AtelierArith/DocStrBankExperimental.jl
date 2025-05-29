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

理想 $a \cdot O$ を返します。ここで、$a$ は `base_ring(O)` の（分数）理想です。
