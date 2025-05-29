```
MinimumRateOfConvergence(rate, order = 1)
```

Checks whether `err[iter] ≥ rate * err[iter - 1]^order` for all `iter ≥ 1`. Since `err[iter] ≥ 0`, this can only be `true` if `rate ≥ 0`. Also, if `order == 1`, it must be the case that `rate ≤ 1` in order for the sequence to not diverge (i.e., to avoid `err[iter] > err[iter - 1]`). In addition, if `err[iter] < 1` for all sufficiently large values of `iter`, it must be the case that `order ≥ 1` for the sequence to not diverge.
