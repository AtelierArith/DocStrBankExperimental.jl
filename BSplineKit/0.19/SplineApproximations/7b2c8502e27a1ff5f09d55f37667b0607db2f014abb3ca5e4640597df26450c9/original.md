```
VariationDiminishing <: AbstractApproxMethod
```

Schoenberg's variation diminishing spline approximation.

Approximates a function $f$ by setting the B-spline coefficients as $c_i = f(x_i)$, where the locations $x_i$ are chosen as the Greville sites:

$$
x_i = \frac{1}{k - 1} ∑_{j = 1}^{k - 1} t_{i + j}.
$$

This method is expected to preserve the shape of the function. However, it may be very inaccurate as an actual approximation of it.

For details, see e.g. de Boor 2001, chapter XI.

!!! warning
    Currently, this method is not guaranteed to work well with recombined B-spline bases (of type [`RecombinedBSplineBasis`](@ref)).

