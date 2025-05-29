```
ideal(O::AlgAssRelOrd, a::AbsSimpleNumFieldOrderFractionalIdeal) -> AlgAssRelOrdIdl
ideal(O::AlgAssRelOrd, a::RelNumFieldOrderFractionalIdeal) -> AlgAssRelOrdIdl
```

Returns the ideal $a \cdot O$ where $a$ is a fractional ideal of `base_ring(O)`.
