```
locally_free_basis(a::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> AlgAssRelOrdElem
```

Returns an element $x$ of the order $O$ of $a$ such that $a_p = O_p \cdot x$ where $p$ is a prime ideal of `base_ring(O)`. See also `is_locally_free`.
