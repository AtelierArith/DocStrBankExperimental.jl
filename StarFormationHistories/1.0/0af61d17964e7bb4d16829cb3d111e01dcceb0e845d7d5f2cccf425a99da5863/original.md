```
calculate_coeffs(MH_model::AbstractMetallicityModel,
                 disp_model::AbstractDispersionModel,
                 mstars::AbstractVector{<:Number}, 
                 logAge::AbstractVector{<:Number},
                 metallicities::AbstractVector{<:Number})
```

Returns per-SSP stellar mass coefficients ($r_{j,k}$ in the [derivation](@ref mzr_derivation)) using the provided metallicity model `MH_model` and metallicity dispersion model `disp_model` for the set of SSPs with logarithmic ages `logAge` and metallicities `metallicities`.

# Examples

```jldoctest; setup = :(import StarFormationHistories: calculate_coeffs, PowerLawMZR, GaussianDispersion)
julia> n_logage, n_mh = 10, 20; # Number of unique logAges, MHs

julia> coeffs = calculate_coeffs(PowerLawMZR(1.0, -1.0),
                                 GaussianDispersion(0.2),
                                 rand(n_logage),
                                 repeat(range(7.0, 10.0; length=n_logage); inner=n_mh),
                                 repeat(range(-2.0, 0.0; length=n_mh); outer=n_logage));

julia> coeffs isa Vector{Float64}
true

julia> length(coeffs) == n_logage * n_mh
true
```
