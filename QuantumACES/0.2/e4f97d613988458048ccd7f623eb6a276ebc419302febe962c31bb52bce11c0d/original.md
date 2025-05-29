```
get_transform(d::Design, est_type::Symbol)
```

Returns a transform matrix that maps gate eigenvalues to gate eigenvalues of type depending on the estimator type `est_type` (`:ordinary`, `:marginal`, or `:relative`), calculated using the gate data of the design `d`.
