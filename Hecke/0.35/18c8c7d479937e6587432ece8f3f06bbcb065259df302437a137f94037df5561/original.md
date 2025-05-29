```
locally_free_basis(O::AlgAssRelOrd, a::AlgAssRelOrdIdl,
                   p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal }) -> AlgAssRelOrdElem
```

Returns an element $x$ of $O$ such that $a_p = O_p \cdot x$ where $p$ is a prime ideal of `base_ring(O)`. It is assumed that $a$ is an ideal of $O$ and $a \subseteq O$. See also `is_locally_free`.
