```
(sampled_masses, sampled_mags) =  generate_stars_mag(mini_vec::AbstractVector{<:Number}, mags, mag_names::AbstractVector{String}, absmag::Real, absmag_name::String, imf::Distributions.Sampleable{Distributions.Univariate,Distributions.Continuous}; dist_mod::Number=0, rng::AbstractRNG=default_rng(), mag_lim::Number=Inf, mag_lim_name::String="V", binary_model::StarFormationHistories.AbstractBinaryModel=RandomBinaryPairs(0.3))
```

Generates a mock stellar population from an isochrone defined by the provided initial stellar masses `mini_vec`, absolute magnitudes `mags`, and filter names `mag_names`. The population is sampled to a total absolute magnitude `absmag::Real` (e.g., -7 or -12) in the filter `absmag_name::String` (e.g., "V" or "F606W") which is contained in the provided `mag_names::AbstractVector{String}`. Other arguments are shared with [`generate_stars_mass`](@ref), which contains the main documentation.

# Notes

## Population Magnitudes

Unlike when sampling a population to a fixed initial birth mass, as is implemented in [`generate_stars_mass`](@ref), when generating a population up to a fixed absolute magnitude, only stars that survive to present-day contribute to the flux of the population. If you choose to limit the apparent magnitude of stars returned by passing the `mag_lim` and `mag_lim_name` keyword arguments, stars fainter than your chosen limit will still be sampled and will still contribute their luminosity to the total population, but they will not be contained in the returned output. 
