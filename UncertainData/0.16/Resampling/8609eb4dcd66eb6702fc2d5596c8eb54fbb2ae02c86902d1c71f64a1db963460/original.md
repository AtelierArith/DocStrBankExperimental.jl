```
resample_elwise(uvd::UVAL_COLLECTION_TYPES, 
    constraint::Union{SamplingConstraint, Vector{SamplingConstraint}},
    n::Int)
```

Resample each element in `uvals` `n` times. The i-th entry in the returned  vector is a `n`-element vector consisting of `n` unique draws of `uvals[i]`, drawn  after first truncating the support of `uvals[i]` according to the provided `constraint`(s).
