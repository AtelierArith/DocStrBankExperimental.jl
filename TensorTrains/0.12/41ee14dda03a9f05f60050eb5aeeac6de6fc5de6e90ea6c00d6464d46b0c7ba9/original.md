```
sample!([rng], x, A::AbstractTensorTrain; r)
```

Draw an exact sample from `A` interpreted as a probability distribution and store the result in `x`. `A` doesn't need to be normalized, however error will be raised if it is found to take negative values.

Optionally specify a random number generator `rng` as the first argument   (defaults to `Random.default_rng()`) and provide a pre-computed `rz = accumulate_R(A)`.

The output is `x, p`, the sampled sequence and its probability
