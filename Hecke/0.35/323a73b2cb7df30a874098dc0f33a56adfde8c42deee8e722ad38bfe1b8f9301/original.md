```
locally_free_basis(O::AlgAssAbsOrd, a::AlgAssAbsOrdIdl,
                   p::Union{ Int, ZZRingElem }) -> AlgAssAbsOrdElem
```

Returns an element $x$ of $O$ such that $a_p = O_p \cdot x$ where $p$ is a prime of $\mathbb Z$. It is assumed that $a$ is an ideal of $O$ and $a \subseteq O$. See also `is_locally_free`.
