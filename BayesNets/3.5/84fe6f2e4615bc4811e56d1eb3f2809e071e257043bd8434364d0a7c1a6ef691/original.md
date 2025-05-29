```
infer(GibbsSampling, state::Assignment, InferenceState)
```

Run Gibbs sampling for `N` iterations. Each iteration changes one node.

Discareds first `burn_in` samples and keeps only the `thin`-th sample. Ex, if `thin=3`, will discard the first two samples and keep the third.
