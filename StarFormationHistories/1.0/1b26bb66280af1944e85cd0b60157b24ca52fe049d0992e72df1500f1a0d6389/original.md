```
(sampled_masses, sampled_mags) = generate_stars_mag_composite(mini_vec::AbstractVector{<:AbstractVector{<:Number}}, mags::AbstractVector, mag_names::AbstractVector{String}, absmag::Number, absmag_name::String, fracs::AbstractVector{<:Number}, imf::Sampleable{Univariate,Continuous}; frac_type::String="lum", kws...)
```

Generates a random sample of stars with a complex star formation history using multiple isochrones. Very similar to [`generate_stars_mag`](@ref) except the isochrone-related arguments `mini_vec` and `mags` should now be vectors of vectors containing the relevant data for the full set of isochrones to be considered. The total absolute magnitude of the sampled population is given by `absmag`. The proportion of the luminosity allotted to each of the individual isochrones is given by the entries of the `frac` vector. This basically just proportions the luminosity according to `frac` and calls [`generate_stars_mag`](@ref) for each of the individual stellar populations; as such it is set up to multi-thread across the multiple stellar populations. 

# Arguments

  * `mini_vec::AbstractVector{<:AbstractVector{<:Number}}` contains the initial masses (in solar masses) for the stars in each isochrone; the internal vectors must be mutable as we will call `Interpolations.deduplicate_knots!` on each. The length of `mini_vec` should be equal to the number of isochrones.
  * `mags` contains the absolute magnitudes from the isochrones in the desired filters corresponding to the same stars as provided in `mini_vec`. The length of `mags` should be equal to the number of isochrones. The individual elements of `mags` are each internally interpreted and converted into a standard format by [`StarFormationHistories.ingest_mags`](@ref). The valid formats for the individual elements of `mags` are:

      * `AbstractVector{AbstractVector{<:Number}}`, in which case the length of the vector `length(mags[i])` can either be equal to `length(mini_vec[i])`, in which case the length of the inner vectors must all be equal to the number of filters you are providing, or the length of the outer vector can be equal to the number of filters you are providing, and the length of the inner vectors must all be equal to `length(mini_vec[i])`; this is the more common use-case.
      * `AbstractMatrix{<:Number}`, in which case `mags[i]` must be 2-dimensional. Valid shapes are `size(mags[i]) == (length(mini_vec[i]), nfilters)` or `size(mags[i]) == (nfilters, length(mini_vec[i]))`, with `nfilters` being the number of filters you are providing.
  * `mag_names::AbstractVector{String}` contains strings describing the filters you are providing in `mags`; an example might be `["B","V"]`. These are used when `mag_lim` is finite to determine what filter you want to use to limit the faintest stars you want returned. These are assumed to be the same for all isochrones.
  * `absmag::Number` gives the total absolute magnitude of the complex population to be sampled.
  * `fracs::AbstractVector{<:Number}` is a vector giving the relative fraction of luminosity or mass (determined by the `frac_type` keyword argument) allotted to each individual stellar population; length must be equal to the length of `mini_vec` and `mags`.
  * `imf::Distributions.Sampleable{Distributions.Univariate, Distributions.Continuous}` is a sampleable continuous univariate distribution implementing a stellar initial mass function with a defined `rand(rng::Random.AbstractRNG, imf)` method to use for sampling masses. All instances of `Distributions.ContinuousUnivariateDistribution` are also valid. Implementations of commonly used IMFs are available in [InitialMassFunctions.jl](https://github.com/cgarling/InitialMassFunctions.jl).

# Keyword Arguments

  * `frac_type::String` either "lum", in which case `fracs` is assumed to contain the relative luminosity fractions for each individual isochrone, or "mass", in which case it is assumed that `fracs` contains mass fractions ("mass" is not yet implemented).

All other keyword arguments `kws...` are passed to [`generate_stars_mag`](@ref); you should refer to that method's documentation for more information. 

# Returns

  * `sampled_masses::Vector{Vector{SVector{N,eltype(imf)}}}` is a vector of vectors containing the initial stellar masses of the sampled stars. The outer vectors are separated by the isochrone the stars were generated from; i.e., all of `sampled_masses[1]` were sampled from `mini_vec[1]` and so on. These can be concatenated into a single vector with `reduce(vcat,sampled_masses)`. The format of the contained `StaticArrays.SVector`s are as output from [`sample_system`](@ref); see that method's documentation for more details.
  * `sampled_mags::Vector{Vector{SVector{N,<:Number}}}` is a vector of vectors containing `StaticArrays.SVectors` with the multi-band magnitudes of the sampled stars. The outer vectors are separated by the isochrone the stars were generated from; i.e. all of `sampled_mags[1]` were sampled from `mags[1]` and so on. To get the magnitude of star `i` in band `j` sampled from isochrone `k`, you would do `sampled_mags[k][i][j]`. This can be concatenated into a `Vector{SVector}` with `reduce(vcat,sampled_mags)` and a 2-D `Matrix` with `reduce(hcat,reduce(vcat,sampled_mags))`.
