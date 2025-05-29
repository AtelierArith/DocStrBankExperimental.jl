```
localization(K::RationalFunctionField{T}, ::typeof(degree)) where T <: FieldElement
```

Return the localization of $k[1/x]$ at $(1/x)$ inside the rational function field $k(x)$, i.e. the localization of the function field at the point at infinity, i.e. the valuation ring for valuation $-$degree$(x)$. This is the ring $k_\infty(x) = \{ f/g | \deg(f) \leq \deg(g)\}$.
