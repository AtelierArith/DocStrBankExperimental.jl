```
rising_factorial(x::ZZRingElem, n::ZZRingElem)
```

Return the rising factorial of $x$, i.e. $x(x + 1)(x + 2)\cdots (x + n - 1)$. If $n < 0$ we throw a `DomainError()`.
