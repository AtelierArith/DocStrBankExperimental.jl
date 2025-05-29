```
infer_current_state(
    hmm::AbstractControlledHMM, obs_sequence, control_sequence, par; safe
)
```

Infer the posterior distribution of the current state given `obs_sequence` for `hmm` with controls `control_sequence` and parameters `par`.

If `safe = true`, everything is done in log scale.
