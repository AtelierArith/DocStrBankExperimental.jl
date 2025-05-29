```
moebius_mu(x::Int)
```

Return the Moebius mu function of $x$ as an `Int`. The value returned is either $-1$, $0$ or $1$. If $x \leq 0$ we throw a `DomainError()`.
