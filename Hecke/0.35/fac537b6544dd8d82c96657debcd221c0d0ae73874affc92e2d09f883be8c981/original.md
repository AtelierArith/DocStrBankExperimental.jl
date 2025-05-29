```
is_locally_free(O::AlgAssRelOrd, a::AlgAssRelOrdIdl,
               p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal }) -> Bool, AlgAssRelOrdElem
```

Returns a tuple `(true, x)` with an element $x$ of $O$ such that $a_p = O_p x$ if $a$ is locally free at $p$, and `(false, 0)` otherwise. $p$ is a prime ideal of `base_ring(O)`. It is assumed that $a$ is an ideal of $O$ and $a \subseteq O$. See also `locally_free_basis`.
