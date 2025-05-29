```
absolute_frobenius(x::FqFieldElem, n = 1)
```

Return the iterated absolute Frobenius $x^{p^n}$, where $p$ is the characteristic of the parent of $x$. By default the Frobenius map is applied $n = 1$ times if $n$ is not specified.
