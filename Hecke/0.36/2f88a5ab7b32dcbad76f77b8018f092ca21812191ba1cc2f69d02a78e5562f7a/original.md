```
is_locally_free(a::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> Bool, AlgAssAbsOrdElem
```

Returns a tuple `(true, x)` with an element $x$ of the order $O$ of $a$ such that $a_p = O_p x$ if $a$ is locally free at $p$, and `(false, 0)` otherwise. $p$ is a prime of $\mathbb Z$. See also `locally_free_basis`.
