```
deriv(loss, output, target) -> Number
```

Compute the analytical derivative with respect to the `output` for the `loss` function. Note that `target` and `output` can be of different numeric type, in which case promotion is performed in the manner appropriate for the given loss.
