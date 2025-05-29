```
roots(f::Generic.Poly{AbsSimpleNumFieldElem}; max_roots = degree(f),
                                ispure = false,
                                is_squarefree = false,
                                is_normal = false)       -> Vector{AbsSimpleNumFieldElem}
```

Computes the roots of a polynomial $f$.

  * `max_roots` controls the maximal number of roots the function returns.
  * `ispure` indicates whether $f$ is of the form $x^d + c$, where $d$ is the degree and $c$ the constant coefficient of $f$.
  * `is_normal` indicates that the field contains no or all the roots of $f$.
  * `is_squarefree` indicated if the polynomial is known to be square free already.
