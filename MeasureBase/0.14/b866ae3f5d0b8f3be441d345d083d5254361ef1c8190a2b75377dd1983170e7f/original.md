```
likelihoodof(k::AbstractTransitionKernel, x; constraints...)
likelihoodof(k::AbstractTransitionKernel, x, constraints::NamedTuple)
```

A likelihood is *not* a measure. Rather, a likelihood acts on a measure, through the "pointwise product" `⊙`, yielding another measure.
