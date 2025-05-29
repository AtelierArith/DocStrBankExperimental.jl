```
world(x::Vector{Float64}, fs::Int)
```

Returns `(f0 = refined_f0, sp = spectrogram, ap = aperiodicity)` after running the full WORLD pipeline consisting of

  * `dio` (f0 extraction)
  * `stonemask` (f0 refinement)
  * `cheaptrick` (spectrogram extraction)
  * `d4c` (aperiodicity extraction)
