```
vals = jac_coord_residual!(nls, x, vals)
```

Computes the Jacobian of the residual at `x` in sparse coordinate format, rewriting `vals`. `rows` and `cols` are not rewritten.
