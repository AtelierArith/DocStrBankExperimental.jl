```
precompute_R2sl([;TRF_min=100e-6, TRF_max=500e-6, T2s_min=5e-6, T2s_max=21e-6, ω1_max=π/TRF_max, B1_max=1.4, greens=greens_superlorentzian])
```

Pre-compute and interpolate the linearized `R2sl(TRF, α, B1, T2s)` and its derivatives `dR2sldB1(TRF, α, B1, T2s)`, `R2sldT2s(TRF, α, B1, T2s)` etc. in the range specified by the arguments.

The function solves the generalized Bloch equations of an isolated semi-solid pool for values in the specified range, calculates the linearized R2sl that minimizes the error of `zs` at the end of the RF-pulse, and interpolates between the different samples.

# Optional Arguments:

  * `TRF_min::Real`: lower bound of the RF-pulse duration range in seconds
  * `TRF_max::Real`: upper bound of the RF-pulse duration range in seconds
  * `T2s_min::Real`: lower bound of the `T2s` range in seconds
  * `T2s_max::Real`: upper bound of the `T2s` range in seconds
  * `ω1_max::Real`: upper bound of the Rabi frequency ω1, the default is the frequency of a 500μs long π-pulse
  * `B1_max::Real`: upper bound of the B1 range, normalized so that `B1 = 1` corresponds to a perfectly calibrated RF field
  * `greens=greens_superlorentzian`: Greens function in the form `G(κ) = G((t-τ)/T2s)`. This package supplies the three Greens functions `greens=greens_superlorentzian` (default), `greens=greens_lorentzian`, and `greens=greens_gaussian`

# Examples

```jldoctest
julia> R2slT = precompute_R2sl();


julia> R2sl, dR2sldB1, R2sldT2s, _ = precompute_R2sl(TRF_min=100e-6, TRF_max=500e-6, T2s_min=5e-6, T2s_max=15e-6, ω1_max=π/500e-6, B1_max=1.4, greens=greens_gaussian);

```
