```
generate_stars_mass(mini_vec::AbstractVector{<:Number},
                    mags, mag_names::AbstractVector{String},
                    limit::Number,
                    imf::Distributions.Sampleable{Distributions.Univariate, Distributions.Continuous};
                    dist_mod::Number=0,
                    rng::Random.AbstractRNG=Random.default_rng(),
                    mag_lim::Number = Inf,
                    mag_lim_name::String = "V",
                    binary_model::StarFormationHistories.AbstractBinaryModel =
                        StarFormationHistories.RandomBinaryPairs(0.3))
```

Generates a random sample of stars from an isochrone defined by the provided initial stellar masses `mini_vec`, absolute magnitudes `mags`, and filter names `mag_names` with total population birth stellar mass `limit` (e.g., 1e5 solar masses). Initial stellar masses are sampled from the provided `imf`. 

# Arguments

  * `mini_vec::AbstractVector{<:Number}` contains the initial masses (in solar masses) for the stars in the isochrone; must be mutable as we call `Interpolations.deduplicate_knots!(mini_vec)`.
  * `mags` contains the absolute magnitudes from the isochrone in the desired filters corresponding to the same stars as provided in `mini_vec`. `mags` is internally interpreted and converted into a standard format by [`StarFormationHistories.ingest_mags`](@ref). Valid inputs are:

      * `mags::AbstractVector{AbstractVector{<:Number}}`, in which case the length of the outer vector `length(mags)` can either be equal to `length(mini_vec)`, in which case the length of the inner vectors must all be equal to the number of filters you are providing, or the length of the outer vector can be equal to the number of filters you are providing, and the length of the inner vectors must all be equal to `length(mini_vec)`; this is the more common use-case.
      * `mags::AbstractMatrix{<:Number}`, in which case `mags` must be 2-dimensional. Valid shapes are `size(mags) == (length(mini_vec), nfilters)` or `size(mags) == (nfilters, length(mini_vec))`, with `nfilters` being the number of filters you are providing.
  * `mag_names::AbstractVector{String}` contains strings describing the filters you are providing in `mags`; an example might be `["B","V"]`. These are used when `mag_lim` is finite to determine what filter you want to use to limit the faintest stars you want returned.
  * `limit::Number` gives the total birth stellar mass of the population you want to sample. See the "Notes" section on population masses for more information.
  * `imf::Distributions.Sampleable{Distributions.Univariate, Distributions.Continuous}` is a sampleable continuous univariate distribution implementing a stellar initial mass function with a defined `rand(rng::Random.AbstractRNG, imf)` method to use for sampling masses. All instances of `Distributions.ContinuousUnivariateDistribution` are also valid. Implementations of commonly used IMFs are available in [InitialMassFunctions.jl](https://github.com/cgarling/InitialMassFunctions.jl).

# Keyword Arguments

  * `dist_mod::Number=0` is the distance modulus (see [`StarFormationHistories.distance_modulus`](@ref)) you wish to have added to the returned magnitudes to simulate a population at a particular distance.
  * `rng::Random.AbstractRNG=Random.default_rng()` is the rng instance that will be used to sample the stellar initial masses from `imf`.
  * `mag_lim::Number=Inf` gives the faintest apparent magnitude for stars you want to be returned in the output. Stars fainter than this magnitude will still be sampled and contribute properly to the total mass of the population, but they will not be returned.
  * `mag_lim_name::String="V"` gives the filter name (as contained in `mag_names`) to use when considering if a star is fainter than `mag_lim`. This is unused if `mag_lim` is infinite.
  * `binary_model::StarFormationHistories.AbstractBinaryModel=StarFormationHistories.RandomBinaryPairs(0.3)` is an instance of a model for treating binaries; currently provided options are [`NoBinaries`](@ref), [`RandomBinaryPairs`](@ref), and [`BinaryMassRatio`](@ref).

# Returns

`(sampled_masses, sampled_mags)` defined as

  * `sampled_masses::Vector{SVector{N,eltype(imf)}}` is a vector containing the initial stellar masses of the stars sampled by [`sample_system`](@ref); see that method's documentation for details on format. In short, each `StaticArrays.SVector` represents one stellar system and each entry in each `StaticArrays.SVector` is one star in that system. Entries will be 0 when companions could have been sampled but were not (i.e., when using a `binary_model` that supports multi-star systems).
  * `sampled_mags::Vector{SVector{N,<:Number}}` is a vector containing `StaticArrays.SVectors` with the multi-band magnitudes of the sampled stars. To get the magnitude of star `i` in band `j`, you index as `sampled_mags[i][j]`. This can be reinterpreted as a 2-dimensional `Matrix` with `reduce(hcat,sampled_mags)`.

# Notes

## Population Masses

Given a particular isochrone with an initial mass vector `mini_vec`, it will never cover the full range of stellar birth masses because stars that die before present-day are not included in the isochrone. However, these stars *were* born, and so contribute to the total birth mass of the system. There are two ways to properly account for this lost mass when sampling:

1. Set the upper limit for masses that can be sampled from the `imf` distribution to a physical value for the maximum birth mass of stars (e.g., 100 solar masses). In this case, these stars will be sampled from `imf`, and will contribute their masses to the system, but they will not be returned if their birth mass is greater than `maximum(mini_vec)`. This is typically easiest for the user and only results in ∼15% loss of efficiency for 10 Gyr isochrones. *This approach is preferred when sampling with binaries.*
2. Set the upper limit for masses that can be sampled from the `imf` distribution to `maximum(mini_vec)` and adjust `limit` to respect the amount of initial stellar mass lost by not sampling higher mass stars. This can be calculated as `new_limit = limit * ( QuadGK.quadgk(x->x*pdf(imf,x), minimum(mini_vec), maximum(mini_vec))[1] / QuadGK.quadgk(x->x*pdf(imf,x), minimum(imf), maximum(imf))[1] )`, with the multiplicative factor being the fraction of the population stellar mass contained in stars with initial masses between `minimum(mini_vec)` and `maximum(mini_vec)`; this factor is the ratio

$$
\frac{\int_a^b \ m \times \frac{dN(m)}{dm} \ dm}{\int_0^∞ \ m \times \frac{dN(m)}{dm} \ dm}.
$$

Note that, if binaries are included, this approach only forms binary pairs between stars whose masses are less than `maximum(mini_vec)`. This is probably not desired, so we recommend the previous approach when including binaries.
