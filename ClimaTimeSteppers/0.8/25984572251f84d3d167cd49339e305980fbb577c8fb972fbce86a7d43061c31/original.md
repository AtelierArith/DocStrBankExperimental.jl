```
MaximumRelativeError(max_rel_err)
```

Checks whether `err[iter] ≤ max_rel_err * val[iter]`. Since `err[iter] ≥ 0` and `val[iter] ≥ 0`, this can only be `true` if `max_rel_err ≥ 0`.
