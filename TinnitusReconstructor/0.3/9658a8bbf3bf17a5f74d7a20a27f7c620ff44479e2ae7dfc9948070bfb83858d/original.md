```
subject_selection_process(stimuli_matrix::AbstractVecOrMat{T}, target_signal::AbstractVector{T}) where {T<:Real}
```

Perform the synthetic subject decision process, given a matrix of precomputed stimuli `stimuli_matrix` and a `target_signal`. The `stimuli_matrix` is of size `m x n` where `m` is the number of trials and `n` is the number of samples in the signal. The `target_signal` is a flat vector of size `n` or an `n x 1` matrix. Return the `n`-dimensional response vector `y` as well as the `stimuli_matrix` as well as `nothing` for the binned representation.
