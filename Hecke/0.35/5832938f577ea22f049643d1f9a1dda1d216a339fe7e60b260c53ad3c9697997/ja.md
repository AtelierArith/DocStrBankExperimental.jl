```
pradical(O::AlgAssRelOrd, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> AlgAssRelOrdIdl
```

理想 $\sqrt{p \cdot O}$ を返します。ここで、$p$ は `base_ring(O)` の素理想です。
