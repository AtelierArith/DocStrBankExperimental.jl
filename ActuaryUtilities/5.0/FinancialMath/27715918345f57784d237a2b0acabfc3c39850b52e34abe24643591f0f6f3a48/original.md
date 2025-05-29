```
spread(curve1,curve2,cashflows)
```

Return the solved-for constant spread to add to `curve1` in order to equate the discounted `cashflows` with `curve2`

# Examples

```julia-repl
spread(0.04, 0.05, cfs)
Rate{Float64, Periodic}(0.010000000000000009, Periodic(1))
```
