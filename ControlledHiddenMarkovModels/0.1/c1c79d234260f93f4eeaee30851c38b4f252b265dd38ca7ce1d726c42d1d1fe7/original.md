```
infer_current_state(hmm::AbstractHMM, obs_sequence, par; safe)
```

Infer the posterior distribution of the current state given `obs_sequence` for `hmm` with parameters `par`.

If `safe = true`, everything is done in log scale.
