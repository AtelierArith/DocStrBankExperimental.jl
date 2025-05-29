```
jacobi_symbol(x::ZZRingElem, y::ZZRingElem)
```

Return the value of the Jacobi symbol $\left(\frac{x}{y}\right)$. The modulus $y$ must be odd and positive, otherwise a `DomainError` is thrown.
