```
exp(M::ProbabilitySimplex, p, X)
```

Compute the exponential map on the probability simplex.

$$
\exp_pX = \frac{1}{2}\Bigl(p+\frac{X_p^2}{\lVert X_p \rVert^2}\Bigr)
+ \frac{1}{2}\Bigl(p - \frac{X_p^2}{\lVert X_p \rVert^2}\Bigr)\cos(\lVert X_p\rVert)
+ \frac{1}{\lVert X_p \rVert}\sqrt{p}\sin(\lVert X_p\rVert),
$$

where $X_p = \frac{X}{\sqrt{p}}$, with its division meant elementwise, as well as for the operations $X_p^2$ and $\sqrt{p}$.
