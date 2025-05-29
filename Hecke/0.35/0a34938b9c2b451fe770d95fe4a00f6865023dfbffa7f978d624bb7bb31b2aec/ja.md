```
ideal(O::AlgAssRelOrd, a::AbsNumFieldOrderIdeal) -> AlgAssRelOrdIdl
ideal(O::AlgAssRelOrd, a::RelNumFieldOrderIdeal) -> AlgAssRelOrdIdl
```

理想 $a \cdot O$ を返します。ここで、$a$ は `base_ring(O)` の理想です。
