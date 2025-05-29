```
baum_welch_multiple_sequences(obs_sequences, hmm_init::HMM[, par; max_iterations, tol])
```

Apply the Baum-Welch algorithm on multiple observation sequences, starting from an initial [`HMM`](@ref) `hmm_init` with parameters `par`.

The parameters are not modified.
