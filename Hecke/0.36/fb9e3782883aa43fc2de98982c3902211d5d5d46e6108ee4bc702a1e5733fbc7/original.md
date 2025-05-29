```
prime_ideals_over(O::AlgAssRelOrd, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> Vector{AlgAssRelOrdIdl}
```

Returns all prime ideals of $O$ lying over $p$ where $p$ is a prime ideal of `base_ring(O)`.
