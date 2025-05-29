```
mod(x::AlgAssRelOrdElem, a::AlgAssRelOrdIdl) -> AlgAssRelOrdElem
```

Returns $y$ in `parent(x)` such that $x \equiv y \mod a$ and the coefficients of $y$ are reduced modulo $a$. Assumes `parent(x) == order(a)` and that $a$ is an integral ideal of `order(a)`.
