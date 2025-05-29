```
PolynomialRatio(b, a)
```

Filter representation in terms of the coefficients of the numerator `b` and denominator `a` of the transfer function:

$$
H(s) = \frac{\verb!b[1]! s^{m-1} + \ldots + \verb!b[m]!}{\verb!a[1]! s^{n-1} + \ldots + \verb!a[n]!}
$$

or equivalently:

$$
H(z) = \frac{\verb!b[1]! + \ldots + \verb!b[n]! z^{-n+1}}{\verb!a[1]! + \ldots + \verb!a[n]! z^{-n+1}}
$$

`b` and `a` may be specified as `Polynomial` objects or vectors ordered from highest power to lowest.
