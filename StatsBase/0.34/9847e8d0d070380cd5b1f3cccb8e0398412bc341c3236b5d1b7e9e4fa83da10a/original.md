```
wsample!([rng], a, w, x; replace=true, ordered=false)
```

Select a weighted sample from an array `a` and store the result in `x`. Sampling probabilities are proportional to the weights given in `w`. `replace` dictates whether sampling is performed with replacement. `ordered` dictates whether an ordered sample (also called a sequential sample, i.e. a sample where items appear in the same order as in `a`) should be taken.

Optionally specify a random number generator `rng` as the first argument (defaults to `Random.default_rng()`).
