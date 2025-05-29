```
subject_selection_process(s::SG, target_signal::AbstractVector{T}, n_trials::I) where {SG<:Stimgen,T<:Real,I<:Integer}
```

Perform the synthetic subject decision process, generating the stimuli on-the-fly using the stimulus generation method `s`.
