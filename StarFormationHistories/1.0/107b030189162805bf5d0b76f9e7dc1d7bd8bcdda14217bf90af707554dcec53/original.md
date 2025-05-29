```
new_mags [, good_idxs] = model_cmd(mags::AbstractVector{<:AbstractVector{<:Number}}, errfuncs, completefuncs; rng::Random.AbstractRNG=Random.default_rng(), ret_idxs::Bool=false)
```

Simple method for modelling photometric error and incompleteness to "mock observe" a pure catalog of stellar photometry, such as those produced by [`generate_stars_mass`](@ref) and [`generate_stars_mag`](@ref). This method assumes Gaussian photometric errors and that the photometric error and completeness functions are separable by filter. 

# Arguments

  * `mags::AbstractVector{<:AbstractVector{<:Number}}`: a vector of vectors giving the magnitudes of each star to be modelled. The first index is the per-star index and the second index is the per-filter index (so `mags[10][2]` would give the magnitude of the tenth star in the second filter). This is the same format as the magnitudes returned by [`generate_stars_mass`](@ref) and [`generate_stars_mag`](@ref); to use output from the composite versions, you must first `reduce(vcat,mags)` before passing to this function.
  * `errfuncs`: an iterable (typically a vector or tuple) of callables (typically functions or interpolators) with length equal to the number of filters contained in the elements of `mags`. This iterable must contain callables that, when called with the associated magnitudes from `mags`, will return the expected 1-σ photometric error at that magnitude. The organization is such that the photometric error for star `i` in band `j` is `σ_ij = errfuncs[j](mags[i][j])`.
  * `completefuncs`: an iterable (typically a vector or tuple) of callables (typically functions or interpolators) with length equal to the number of filters contained in the elements of `mags`. This iterable must contain callables that, when called with the associated magnitudes from `mags`, will return the probability that a star with that magnitude in that band will be found in your color-magnitude diagram (this should include the original detection probability and any post-detection quality, morphology, or other cuts). The organization is such that the detection probability for star `i` in band `j` is `c_ij = completefuncs[j](mags[i][j])`.

# Keyword Arguments

  * `rng::AbstractRNG=Random.default_rng()`: The object to use for random number generation.
  * `ret_idxs::Bool`: whether to return the indices of the input `mags` for the stars that were successfully "observed" and are represented in the output `new_mags`.

# Returns

  * `new_mags`: an object similar to `mags` (i.e., a `Vector{Vector{<:Number}}`, `Vector{SVector{N,<:Number}}`, etc.) containing the magnitudes of the mock-observed stars. This will be shorter than the provided `mags` vector as we are modelling photometric incompleteness, and the magnitudes will also have random photometric errors added to them. This can be reinterpreted as a 2-dimensional `Matrix` with `reduce(hcat,new_mags)`.
  * `good_idxs`: if `ret_idxs` is `true`, the vector of indices into the input `mags` for the stars that were successfully "observed" and are represented in the output `new_mags`.

# Notes

  * This is a simple implementation that seeks to show a simple example of how one can post-process catalogs of "pure" stars from methods like [`generate_stars_mass`](@ref) and [`generate_stars_mag`](@ref) to include observational effects. This method assumes Gaussian photometric errors, which may not, in general, be accurate. It also assumes that the total detection probability can be modelled as the product of the single-filter detection probabilities as computed by `completefuncs` (i.e., that the completeness functions are separable across filters). This can be a reasonable assumption when you have separate photometric catalogs derived for each filter and you only collate them afterwards, but it is generally not a good assumption for detection algorithms that operate on simultaneously on multi-band photometry – the completeness functions for these types of algorithms are generally not separable.
