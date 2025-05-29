```
roots(x::AcbPolyRingElem; target=0, isolate_real=false, initial_prec=0, max_prec=0, max_iter=0)
```

Attempts to isolate the complex roots of the complex polynomial $x$ by iteratively refining balls in which they lie.

This is done by increasing the working precision, starting at `initial_prec`. The maximal number of iterations can be set using `max_iter` and the maximal precision can be set using `max_prec`.

If `isolate_real` is set and $x$ is strictly real, then the real roots will be isolated from the non-real roots. Every root will have either zero, positive or negative real part.

It is assumed that $x$ is squarefree.
