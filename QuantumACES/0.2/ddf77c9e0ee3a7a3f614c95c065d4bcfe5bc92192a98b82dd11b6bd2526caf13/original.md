```
get_diag_design(d::Design; diagnostics::Bool = false)
```

Returns a copy of the design `d` where the covariance matrix dictionary generates a diagonal covariance matrix, printing diagnostics if `diagnostics` is `true`.
