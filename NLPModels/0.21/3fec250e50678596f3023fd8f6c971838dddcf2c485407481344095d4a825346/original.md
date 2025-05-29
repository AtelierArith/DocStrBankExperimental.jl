```
Jtv = jtprod_residual!(nls, x, v, Jtv)
```

Computes the product of the transpose of the Jacobian of the residual at x and a vector, i.e.,  $J(x)^Tv$, storing it in `Jtv`.
