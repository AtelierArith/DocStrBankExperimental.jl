```
struct MiniBatchContext{Tctx, T} <: AbstractContext
    context::Tctx
    loglike_scalar::T
end
```

The `MiniBatchContext` enables the computation of `log(prior) + s * log(likelihood of a batch)` when running the model, where `s` is the `loglike_scalar` field, typically equal to `the number of data points / batch size`. This is useful in batch-based stochastic gradient descent algorithms to be optimizing `log(prior) + log(likelihood of all the data points)` in the expectation.
