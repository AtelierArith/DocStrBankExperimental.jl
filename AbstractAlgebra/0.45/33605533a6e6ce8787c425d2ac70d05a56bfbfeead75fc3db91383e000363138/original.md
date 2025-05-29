```
is_separable(f::PolyRingElem) -> Bool
```

Return whether for a polynomial $f$ over a ring $R$ the quotient ring $R[x]/(f)$ is separable over $R$. If $R$ is a field, this is equivalent to $f$ having no repeated roots in an algebraic closure, or to $f$ being coprime to the formal derivative $f'$.
