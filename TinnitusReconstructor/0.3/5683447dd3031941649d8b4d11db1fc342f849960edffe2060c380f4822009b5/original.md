```
generate_stimuli_matrix(s::BS, n_trials::I) where {BS<:BinnedStimgen, I<:Integer}
```

Generate `n_trials` of stimuli based on specifications in the stimgen type.

Returns `stimuli_matrix`, `Fs`, `spect_matrix`, `binned_repr_matrix`. 
