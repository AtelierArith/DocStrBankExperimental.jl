```
ideal(O::AlgAssRelOrd, a::AbsSimpleNumFieldOrderFractionalIdeal) -> AlgAssRelOrdIdl
ideal(O::AlgAssRelOrd, a::RelNumFieldOrderFractionalIdeal) -> AlgAssRelOrdIdl
```

理想 $a \cdot O$ を返します。ここで、$a$ は `base_ring(O)` の分数理想です。
