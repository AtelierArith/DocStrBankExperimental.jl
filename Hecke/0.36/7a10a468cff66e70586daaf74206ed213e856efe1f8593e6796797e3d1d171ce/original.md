```
divexact_right(a::AlgAssAbsOrdElem, b::AlgAssAbsOrdElem; check::Bool = true)
divexact_right(a::AlgAssRelOrdElem, b::AlgAssRelOrdElem; check::Bool = true)
  -> AlgAssRelOrdElem
```

Returns an element $c \in O$ such that $a = c \cdot b$ where $O$ is the order containing $a$. If `check` is `false`, it is not checked whether $c$ is an element of $O$.
