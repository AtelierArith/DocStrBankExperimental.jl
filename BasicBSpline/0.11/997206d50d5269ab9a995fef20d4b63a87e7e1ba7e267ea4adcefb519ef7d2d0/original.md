```
bsplinebasis′₋₀(::AbstractFunctionSpace, ::Integer, ::Real) -> Real
```

1st derivative of B-spline basis function. Left-sided limit version.

$$
\dot{B}_{(i,p,k)}(t)
=p\left(\frac{1}{k_{i+p}-k_{i}}B_{(i,p-1,k)}(t)-\frac{1}{k_{i+p+1}-k_{i+1}}B_{(i+1,p-1,k)}(t)\right)
$$

`bsplinebasis′₋₀(P, i, t)` is equivalent to `bsplinebasis₋₀(derivative(P), i, t)`.
