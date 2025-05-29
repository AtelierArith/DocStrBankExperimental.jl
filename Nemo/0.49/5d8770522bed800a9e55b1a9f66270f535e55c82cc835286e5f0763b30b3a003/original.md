```
frobenius(x::FqFieldElem, n = 1)
```

Return the iterated Frobenius $x^{q^n}$ of an element $x$, where $q$ is the order of the base field. By default the Frobenius map is applied $n = 1$ times if $n$ is not specified.
