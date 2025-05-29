```
locally_free_basis(a::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> AlgAssAbsOrdElem
```

Returns an element $x$ of the order $O$ of $a$ such that $a_p = O_p \cdot x$ where $p$ is a prime of $\mathbb Z$. See also `is_locally_free`.
