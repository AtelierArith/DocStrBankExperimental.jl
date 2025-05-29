```
logdensityof(hmm::AbstractControlledHMM, obs_sequence, control_sequence, par; safe)
```

Compute the log likelihood of `obs_sequence` for `hmm` with controls `control_sequence` and parameters `par`.

If `safe = true`, everything is done in log scale.
