```
stratified_cv = StratifiedCV(; nfolds=6,
                               shuffle=false,
                               rng=Random.GLOBAL_RNG)
```

Stratified cross-validation resampling strategy, for use in `evaluate!`, `evaluate` and in tuning. Applies only to classification problems (`OrderedFactor` or `Multiclass` targets).

```julia
train_test_pairs(stratified_cv, rows, y)
```

Returns an `nfolds`-length iterator of `(train, test)` pairs of vectors (row indices) where each `train` and `test` is a sub-vector of `rows`. The `test` vectors are mutually exclusive and exhaust `rows`. Each `train` vector is the complement of the corresponding `test` vector.

Unlike regular cross-validation, the distribution of the levels of the target `y` corresponding to each `train` and `test` is constrained, as far as possible, to replicate that of `y[rows]` as a whole.

The stratified `train_test_pairs` algorithm is invariant to label renaming. For example, if you run `replace!(y, 'a' => 'b', 'b' => 'a')` and then re-run `train_test_pairs`, the returned `(train, test)` pairs will be the same.

Pre-shuffling of `rows` is controlled by `rng` and `shuffle`. If `rng` is an integer, then the `StratifedCV` keywod constructor resets it to `MersenneTwister(rng)`. Otherwise some `AbstractRNG` object is expected.

If `rng` is left unspecified, `rng` is reset to `Random.GLOBAL_RNG`, in which case rows are only pre-shuffled if `shuffle=true` is explicitly specified.
