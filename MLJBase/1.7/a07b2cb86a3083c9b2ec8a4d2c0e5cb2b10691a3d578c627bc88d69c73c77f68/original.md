```
holdout = Holdout(; fraction_train=0.7, shuffle=nothing, rng=nothing)
```

Instantiate a `Holdout` resampling strategy, for use in `evaluate!`, `evaluate` and in tuning.

```julia
train_test_pairs(holdout, rows)
```

Returns the pair `[(train, test)]`, where `train` and `test` are vectors such that `rows=vcat(train, test)` and `length(train)/length(rows)` is approximatey equal to fraction_train`.

Pre-shuffling of `rows` is controlled by `rng` and `shuffle`. If `rng` is an integer, then the `Holdout` keyword constructor resets it to `MersenneTwister(rng)`. Otherwise some `AbstractRNG` object is expected.

If `rng` is left unspecified, `rng` is reset to `Random.GLOBAL_RNG`, in which case rows are only pre-shuffled if `shuffle=true` is specified.
