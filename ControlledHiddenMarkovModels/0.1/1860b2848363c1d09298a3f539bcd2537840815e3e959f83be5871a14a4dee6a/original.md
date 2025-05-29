```
logdensityof(hmm::AbstractHMM, obs_sequence, par; safe)
```

Compute the log likelihood of `obs_sequence` for `hmm` with parameters `par`.

If `safe = true`, everything is done in log scale.
