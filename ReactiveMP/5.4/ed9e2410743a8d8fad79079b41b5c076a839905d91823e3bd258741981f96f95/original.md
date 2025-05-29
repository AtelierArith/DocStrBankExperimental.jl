Initialization of the BIFMMeta object can be performed by calling

```julia
meta = BIFMMeta(A, B, C, μu, Σu)
```

where `A`, `B` and `C` are the transition matrices in the model. `μu` and `Σu` are the mean vector and covariance matrix of the input. Importantly, in this setting we assume that these are known and do not change due to an external model.
