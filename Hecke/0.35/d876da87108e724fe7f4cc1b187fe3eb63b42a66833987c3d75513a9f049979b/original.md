```
is_locally_free(O::AlgAssAbsOrd, a::AlgAssAbsOrdIdl, p::ZZRingElem
               side = :right) -> Bool, AlgAssAbsOrdElem
```

Returns a tuple `(true, x)` with an element $x$ of $O$ such that $a O_p = x O_p$ resp. $O_p a = O_p x$ if $a$ is locally free right (resp. left) ideal at $p$, and `(false, 0)` otherwise.  It is assumed that $a$ is an ideal of $O$ and $a \subseteq O$.

See also `locally_free_basis`.
