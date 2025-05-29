```
tilde_observe(context::SamplingContext, right, left, vi)
```

Handle observed constants with a `context` associated with a sampler.

Falls back to `tilde_observe(context.context, context.sampler, right, left, vi)`.
