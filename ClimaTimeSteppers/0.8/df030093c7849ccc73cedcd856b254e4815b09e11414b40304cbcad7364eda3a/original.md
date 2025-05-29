```
MaximumErrorReduction(max_reduction)
```

Checks whether `err[iter] ≤ max_reduction * err[0]` for all `iter ≥ 1`. Since `err[iter] ≥ 0`, this can only be `true` if `max_reduction ≥ 0`. Also, it must be the case that `max_reduction ≤ 1` in order for the sequence to not diverge (i.e., to avoid `err[iter] > err[0]`).
