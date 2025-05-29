```
evaluate_and_gradient!(u, f::Polynomial, x)
```

Evaluate the polynomial `f` and its gradient at `x`. Stores the gradient in `u` and returns the `f(x)`.

```
evaluate_and_gradient!(u, f::Polynomial, x, p)
```

Evaluate the polynomial `f` and its gradient at `x` with parameters `p`. Stores the gradient in `u` and returns the `f(x)`.
