```
to_univariate(p::MPolyRingElem)
```

Assuming the polynomial $p$ is actually a univariate polynomial in the variable $x$, convert the polynomial to a univariate polynomial in a univariate polynomial ring over the same base ring in the variable $x$. If $p$ is constant, it is considered to be a polynomial in the first variable of its parent. An exception is raised if the polynomial $p$ involves more than one variable or if its parent has no variables.
