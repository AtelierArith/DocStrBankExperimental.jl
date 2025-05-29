```
Parms(; kwargs...) -> Parms
```

ACT-R parameters with default values. Default values are overwritten with keyword arguments.

# Fields

  * `d=0.5`: activation decay
  * `τ=0.0`: retrieval threshold
  * `s=0.2`: logistic scalar for activation noise.
  * `γ=1.6`: maximum associative strength
  * `δ=0.0`: mismatch penalty
  * `ω=1.0`: weight for source of spreading activation
  * `blc=0.0`: base level constant
  * `ter=0.0`: a constant for encoding and responding time
  * `dissim_func`: computes dissimilarity between two slot values. Output ranges from 0 (maximally similar) to 1 (maximially dissimilar)
  * `sa_fun`: a function for spreading activation which requires arguments for actr and chunk
  * `util_mmp_fun`: utility mismatch penalty function applied to each condition
  * `lf=1.0:` latency factor parameter
  * `u0=0.0`: initial utility value
  * `σu=.2`: standard deviation of utility noise
  * `δu=1.0`: mismatch penalty parameter for utility
  * `τu0 = -100`: initial value of utility threshold
  * `τu = τu0`: utility threshold
  * `u0Δ = 1.0`: utility decrement
  * `τuΔ = 1.0`: utility threshold decrement
  * `utility_decrement=1.0`: the utility decrement scalar. After each microlapse, `utility_decrement` is multiplied by u0Δ
  * `threshold_decrement=1.0`: the threshold decrement scalar. After each microlapse, `threshold_decrement` is multiplied by τuΔ
  * `bll=false`: base level learning on
  * `mmp=false`: mismatch penalty on
  * `sa=false`: spreading activatin on
  * `noise=false`: noise on
  * `mmp_utility=false`: mismatch penalty for procedural memory
  * `utility_noise=false`: utility noise for procedural memory
  * `tmp=s * √(2)`: temperature for blending
  * `misc`: `NamedTuple` of extra parameters
  * `filtered:` a list of slots that must absolutely match with mismatch penalty. `isa` and `retrieval` are included   by default
