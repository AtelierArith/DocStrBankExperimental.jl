```
divexact_left(a::AlgAssAbsOrdElem, b::AlgAssAbsOrdElem; check::Bool = true)
divexact_left(a::AlgAssRelOrdElem, b::AlgAssRelOrdElem; check::Bool = true)
  -> AlgAssRelOrdElem
```

Returns an element $c \in O$ such that $a = b \cdot c$ where $O$ is the order containing $a$. If `check` is `false`, it is not checked whether $c$ is an element of $O$.
