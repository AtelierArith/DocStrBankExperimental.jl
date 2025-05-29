```
Epicompose(L, f, [mu])
```

Return the epi-composition of $f$ with $L$, also known as infimal postcomposition or image function. Given a function f and a linear operator L, their epi-composition is:

$$
g(y) = (Lf)(y) = inf_x { f(x) : Lx = y }
$$

This is the dual operation to precomposition, see Rockafellar and Wets, "Variational Analysis", Theorem 11.23.

If $mu > 0$ is specified, then $L$ is assumed to be such that $L'*L == mu*I$, and the proximal operator is computable for any convex $f$. If $mu$ is not specified, then $f$ must be of $Quadratic$ type.
