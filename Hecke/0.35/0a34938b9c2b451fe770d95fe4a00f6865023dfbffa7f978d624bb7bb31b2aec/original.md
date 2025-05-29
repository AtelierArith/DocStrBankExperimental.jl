```
ideal(O::AlgAssRelOrd, a::AbsNumFieldOrderIdeal) -> AlgAssRelOrdIdl
ideal(O::AlgAssRelOrd, a::RelNumFieldOrderIdeal) -> AlgAssRelOrdIdl
```

Returns the ideal $a \cdot O$ where $a$ is an ideal of `base_ring(O)`.
