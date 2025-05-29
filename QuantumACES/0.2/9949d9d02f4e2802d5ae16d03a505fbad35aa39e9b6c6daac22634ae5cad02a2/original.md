```
get_wht_transform(d::Design, est_type::Symbol; inverse::Bool = false)
```

Returns a transform matrix that maps padded gate error probabilities to padded gate eigenvalues, or the inverse transform if `inverse` is `true`, whose type depends on the estimator type `est_type` (`:ordinary`, :marginal`, or`:relative`), calculated using the gate data of the design`d`.
