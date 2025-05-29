```
rcond = oprcondest(op; exact = false)
```

Compute `rcond`, an estimation of the `1`-norm reciprocal condition number of a linear operator `op`, where `op` is one of the defined Lyapunov or Sylvester operators. The estimate is computed as $\text{rcond} = 1 / (\|op\|_1\|inv(op)\|_1)$, using estimates of the `1`-norm, if `exact = false`, or computed exact values of the `1`-norm, if `exact = true`. The `exact = true` option is not recommended for large order operators.
