```
inds = align_signals(s::AbstractVector{<:AbstractArray}, master = argmax(length.(s)); method = :dtw, output=:indices)
```

Compute a set of indices such that `s[i][inds[i]]` is optimally aligned to `s[master]`. All elements of `inds` will have the same length.

# Arguments:

  * `s`: A vector of signals to align
  * `master`: Index of the signal used as reference. All the other signals will be aligned to this one.
  * `method`: `:dtw` uses the warping paths from dtw between `s[master]` and `s[i]`. `:xcorr` uses `DSP.finddelay` which internally computes the cross correlation between signals, which often results in a slight misalignment.
  * `output`: The default is to output the aligning indices, alternatively, the aligned `:signals` themselves can be outputted.
