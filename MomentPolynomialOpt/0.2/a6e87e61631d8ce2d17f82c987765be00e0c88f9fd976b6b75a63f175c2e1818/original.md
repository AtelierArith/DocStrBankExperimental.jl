```
K,I,P,B = annihilator(sigma::Series{R}, L, eqzero = is_zero)
```

Compute a graded basis of the annihilator of the positive series $σ$ in the space spanned by the list of monomials L.

It outputs:

  * K the graded basis
  * I the initial monomials of K
  * P the orthogonal basis
  * B the monomial basis
