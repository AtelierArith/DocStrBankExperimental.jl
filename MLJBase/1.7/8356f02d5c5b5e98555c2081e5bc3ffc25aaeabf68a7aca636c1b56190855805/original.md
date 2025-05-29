```
cv = CV(; nfolds=6,  shuffle=nothing, rng=nothing)
```

Cross-validation resampling strategy, for use in `evaluate!`, `evaluate` and tuning.

```julia
train_test_pairs(cv, rows)
```

Returns an `nfolds`-length iterator of `(train, test)` pairs of vectors (row indices), where each `train` and `test` is a sub-vector of `rows`. The `test` vectors are mutually exclusive and exhaust `rows`. Each `train` vector is the complement of the corresponding `test` vector. With no row pre-shuffling, the order of `rows` is preserved, in the sense that `rows` coincides precisely with the concatenation of the `test` vectors, in the order they are generated. The first `r` test vectors have length `n + 1`, where `n, r = divrem(length(rows), nfolds)`, and the remaining test vectors have length `n`.

Pre-shuffling of `rows` is controlled by `rng` and `shuffle`. If `rng` is an integer, then the `CV` keyword constructor resets it to `MersenneTwister(rng)`. Otherwise some `AbstractRNG` object is expected.

If `rng` is left unspecified, `rng` is reset to `Random.GLOBAL_RNG`, in which case rows are only pre-shuffled if `shuffle=true` is explicitly specified.
