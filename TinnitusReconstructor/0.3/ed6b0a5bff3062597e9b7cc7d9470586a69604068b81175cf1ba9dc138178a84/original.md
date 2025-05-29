```
generate_stimuli_matrix(s::SG, n_trials::I) where {SG<:Stimgen, I<:Integer}
```

Generate `n_trials` of stimuli based on specifications in the stimgen type.

Returns `stimuli_matrix`, `Fs`, `spect_matrix`, `binned_repr_matrix`.      `binned_repr_matrix` = nothing if s >: BinnedStimgen.
