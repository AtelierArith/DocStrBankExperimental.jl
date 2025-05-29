# Riemann Liouville sense fractional integral approximation.

```
fracint(f, α, end_point, h, RLIntApprox())
```

### Example

```julia-repl
julia> fracint(x->x^5, 0.5, 2.5, 0.0001, RLIntApprox())
64.36229646291393
```

Using the **Staircase approximation** to approximate the original function and implement the summation.
