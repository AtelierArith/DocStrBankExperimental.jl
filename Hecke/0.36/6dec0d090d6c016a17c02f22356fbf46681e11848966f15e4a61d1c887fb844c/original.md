```
is_locally_free(a::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> Bool, AlgAssRelOrdElem
```

Returns a tuple `(true, x)` with an element $x$ of the order $O$ of $a$ such that $a_p = O_p x$ if $a$ is locally free at $p$, and `(false, 0)` otherwise. $p$ is a prime ideal of `base_ring(O)`. See also `locally_free_basis`.
