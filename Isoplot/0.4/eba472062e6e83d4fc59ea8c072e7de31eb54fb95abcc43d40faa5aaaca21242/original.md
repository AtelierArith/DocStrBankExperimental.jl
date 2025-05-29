```julia
wμ, wσ, mswd = wmean(μ, σ; corrected=true, chauvenet=false)
wμ ± wσ, mswd = wmean(μ ± σ; corrected=true, chauvenet=false)
```

The weighted mean, with or without the "geochronologist's MSWD correction" to uncertainty. You may specify your means and standard deviations either as separate vectors `μ` and `σ`, or as a single vector `x` of `Measurement`s equivalent to `x = μ .± σ`

In all cases, `σ` is assumed to reported as *actual* sigma (i.e., 1-sigma).

If `corrected=true`, the resulting uncertainty of the weighted mean is expanded by a factor of `sqrt(mswd)` to attempt to account for dispersion dispersion when the MSWD is greater than `1`

If `chauvenet=true`, outliers will be removed before the computation of the weighted mean  using Chauvenet's criterion.

### Examples

```julia
julia> x = randn(10)
10-element Vector{Float64}:
  0.4612989881720301
 -0.7255529837975242
 -0.18473979056481055
 -0.4176427262202118
 -0.21975911391551833
 -1.6250003193791873
 -1.6185557291787287
  0.25315988825847513
 -0.4979804844182867
  1.3565281078086726

julia> y = ones(10);

julia> wmean(x, y)
(-0.321824416323509, 0.31622776601683794, 0.8192171477885678)

julia> wmean(x .± y)
(-0.32 ± 0.32, 0.8192171477885678)

julia> wmean(x .± y./10)
(-0.322 ± 0.032, 81.9217147788568)

julia> wmean(x .± y./10, corrected=true)
(-0.32 ± 0.29, 81.9217147788568)
```
