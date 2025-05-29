```
spolynomial(p::AbstractPolynomialLike, q::AbstractPolynomialLike)
```

Computes the S-polynomial of `p` and `q` defined by

$$
S(p, q) =  \frac{m}{\mathrm{\mathsc{LT}}(p)} \cdot p - \frac{m}{\mathrm{\mathsc{LT}}(q)} \cdot q
$$

where $m = \mathrm{lcm}(\mathrm{\mathsc{LM}}(p), \mathrm{\mathsc{LM}}(q))$.
