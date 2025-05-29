```
sample!([rng], a, [wv::AbstractWeights], x; replace=true, ordered=false)
```

Draw a random sample of `length(x)` elements from an array `a` and store the result in `x`. A polyalgorithm is used for sampling. Sampling probabilities are proportional to the weights given in `wv`, if provided. `replace` dictates whether sampling is performed with replacement. `ordered` dictates whether an ordered sample (also called a sequential sample, i.e. a sample where items appear in the same order as in `a`) should be taken.

Optionally specify a random number generator `rng` as the first argument (defaults to `Random.default_rng()`).

Output array `a` must not be the same object as `x` or `wv` nor share memory with them, or the result may be incorrect.
