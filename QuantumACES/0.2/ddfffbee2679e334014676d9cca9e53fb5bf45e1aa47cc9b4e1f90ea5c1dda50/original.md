```
get_pad_transform(d::Design, est_type::Symbol; probabilities::Bool = false)
```

Returns a transform matrix that pads gate eigenvalues, or gate error probabilities if `probabilities` is `true`, whose type depends on the estimator type `est_type` (`:ordinary`, `:marginal`, or `:relative`), with identity eigenvaleus or error probabilities, respectively, calculated using the gate data of the design `d`.
