```
PrecomposeDiagonal(f, a, b)
```

Return the function

$$
g(x) = f(\mathrm{diag}(a)x + b)
$$

Function $f$ must be convex and separable, or `a` must be a scalar, for the `prox` of $g$ to be computable. Parametes `a` and `b` can be arrays of multiple dimensions, according to the shape/size of the input `x` that will be provided to the function: the way the above expression for $g$ should be thought of, is `g(x) = f(a.*x + b)`.
