```
hrf(;
TR = 1,
peak = 6.0,
post_undershoot = 16,
length = 32.0,
peak_width = 1.0,
post_undershoot_width = 1,
amplitude = 6,
shift = 0)
```

Generate a parameterized BOLD haemodynamic response function (HRF) kernel based on gamma-functions.

Implementation and default parameters were taken from the SPM-toolbox.

Note: TR = 1/sfreq

# Keyword arguments

  * `TR = 1`: repetition time, 1/sfreq.
  * `length = 32.0`: total length of the kernel in seconds.
  * `amplitude = 6`: maximal amplitude.
  * `peak = 6.0`: peak timing.
  * `peak_width = 1.0`: width of the peak.
  * `post_undershoot = 16`: post-undershoot timing.
  * `post_undershoot_width = 1`: post-undershoot width.
  * `shift = 0`: shift the whole HRF.

# Returns

  * `Vector`: HRF BOLD response.

# Examples

```julia-repl
julia> hrf()
33-element Vector{Float64}:
  0.0
  0.0007715994433635659
  0.019784004131204957
  0.08202939459091822
  0.158157713522699
  ⋮
 -0.0006784790038792572
 -0.00042675060451877775
 -0.000263494738348278
 -0.00015990722628360688
 -9.548780093799345e-5
```
