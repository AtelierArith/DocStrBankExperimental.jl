```
tilde_assume(context::SamplingContext, right, vn, vi)
```

Handle assumed variables, e.g., `x ~ Normal()` (where `x` does occur in the model inputs), accumulate the log probability, and return the sampled value with a context associated with a sampler.

Falls back to

```julia
tilde_assume(context.rng, context.context, context.sampler, right, vn, vi)
```
