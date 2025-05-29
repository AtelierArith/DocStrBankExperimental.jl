```
evaluate_all(
    B::AbstractBSplineBasis, x::Real,
    [op = Derivative(0)], [T = float(typeof(x))];
    [ileft = nothing],
) -> i, bs
```

Evaluate all B-splines which are non-zero at coordinate `x`.

Returns a tuple `(i, bs)`, where `i` is an index identifying the basis functions that were computed, and `bs` is a tuple with the actual values.

More precisely:

  * `i` is the index of the first B-spline knot $t_{i}$ when going from $x$ towards the left. In other words, it is such that $t_{i} ≤ x < t_{i + 1}$.

    It can be effectively computed as `i = searchsortedlast(knots(B), x)`. If the correct value of `i` is already known, one can avoid this computation by manually passing this index via the optional `ileft` keyword argument.
  * `bs` is a tuple of B-splines evaluated at $x$:

    $$
    (b_i(x), b_{i - 1}(x), …, b_{i - k + 1}(x)).
    $$

    It contains $k$ values, where $k$ is the order of the B-spline basis. Note that values are returned in backwards order starting from the $i$-th B-spline.

## Computing derivatives

One can pass the optional `op` argument to compute B-spline derivatives instead of the actual B-spline values.

## Examples

See [`AbstractBSplineBasis`](@ref) for some examples using the alternative evaluation syntax `B(x, [op], [T]; [ileft])`, which calls this function.
