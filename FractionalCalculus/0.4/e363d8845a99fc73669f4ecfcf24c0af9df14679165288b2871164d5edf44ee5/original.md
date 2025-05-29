# Riemann Liouville sense fractional integral using piecewise interpolation.

```
fracint(f, α, end_point, h, RLPiecewise())
```

### Example

```julia-repl
julia> fracint(x->x^5, 0.5, 2.5, 0.0001, RLPiecewise())
64.36234206345209
```

By deploying Piecewise interpolation to approximate the original function, with small step size, this method is fast and take little memory allocation.

Using piecewise linear interpolation:

$$
    y_n(t)=\frac{t-t_{i+1}}{t_i-t_{i+1}}y(t_i)+\frac{t-t_i}{t_{i+1}-t_i}y(t_{i+1})
$$

Constitute the original function with the interpolation and implement the summation.
