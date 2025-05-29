```
SignCoherence(reference[; name=:coherence]) <: PostStepStrategy
```

After each step, compute the proportion of configurations that have the same sign as they do in the `reference_dvec`. Reports to a column named `name`, which defaults to `coherence`.
