```
result::StatsBase.Histogram =
    partial_cmd_smooth(m_ini::AbstractVector{<:Number},
                       mags::AbstractVector{<:AbstractVector{<:Number}},
                       mag_err_funcs,
                       y_index,
                       color_indices,
                       imf,
                       completeness_funcs=[one for i in mags];
                       dmod::Number=0,
                       normalize_value::Number=1,
                       binary_model::AbstractBinaryModel=NoBinaries(),
                       mean_mass=mean(imf),
                       edges=nothing,
                       xlim=nothing,
                       ylim=nothing,
                       nbins=nothing,
                       xwidth=nothing,
                       ywidth=nothing)
```

Main function for generating template Hess diagrams from a simple stellar population of stars from an isochrone, including photometric error and completeness.

# Arguments

  * `m_ini::AbstractVector{<:Number}` is a vector containing the initial stellar masses of the stars from the isochrone.
  * `mags::AbstractVector{<:AbstractVector{<:Number}}` is a vector of vectors. Each constituent vector with index `i` should have `length(mags[i]) == length(m_ini)`, representing the magnitudes of the isochrone stars in each of the magnitudes considered. In most cases, mags should contain 2 (if y-axis mag is also involved in the x-axis color) or 3 vectors.
  * `mag_err_funcs` must be an indexable object (e.g., a `Vector` or `Tuple`) that contains callables (e.g., a `Function`) to compute the 1σ photometric errors for the same filters provided in `mags`. Each callable must take a single argument (an *apparent* magnitude) and return a `Number`. The length `mag_err_funcs` must be equal to the length of `mags`.
  * `y_index` gives a valid index (e.g., an `Int` or `CartesianIndex`) into `mags` for the filter you want to have on the y-axis of the Hess diagram. For example, if the `mags` argument contains the B and V band magnitudes as `mags=[B, V]` and you want V on the y-axis, you would set `y_index` as `2`.
  * `color_indices` is a length-2 indexable object giving the indices into `mags` that are to be used to compute the x-axis color. For example, if the `mags` argument contains the B and V band magnitudes as `mags=[B, V]`, and you want B-V to be the x-axis color, then `color_indices` should be `[1,2]` or `(1,2)` or similar.
  * `imf` is a callable that takes an initial stellar mass as its sole argument and returns the (properly normalized) probability density of your initial mass function model. All the models from [InitialMassFunctions.jl](https://github.com/cgarling/InitialMassFunctions.jl) are valid for `imf`.
  * `completeness_functions` must be an indexable object (e.g., a `Vector` or `Tuple`) that contains callables (e.g., a `Function`) to compute the single-filter completeness fractions as a function of *apparent* magnitude. Each callable in this argument must correspond to the matching filter provided in `mags`.

# Keyword Arguments

  * `dmod::Number=0` is the distance modulus in magnitudes to apply to the input `mags`. Leave at `0` if you are providing apparent magnitudes in `mags`.
  * `normalize_value::Number=1` is the total stellar mass of the population you wish to model.
  * `binary_model::AbstractBinaryModel=NoBinaries()` is the model to use for including binary systems. Currently only [`StarFormationHistories.NoBinaries`](@ref) and [`StarFormationHistories.RandomBinaryPairs`](@ref) are supported.
  * `mean_mass::Number` is the expectation value of the initial mass for a random star drawn from your provided `imf`. This will be computed for you if your provided `imf` is a valid continuous, univariate `Distributions.Distribution` object.
  * `edges` is a tuple of ranges defining the left-side edges of the bins along the x-axis (`edges[1]`) and the y-axis (`edges[2]`). Example: `(-1.0:0.1:1.5, 22:0.1:27.2)`. If `edges` is provided, it overrides the following keyword arguments that offer other ways to specify the extent of the Hess diagram.
  * `xlim` is a length-2 indexable object (e.g., a `Vector` or `Tuple`) giving the lower and upper bounds on the x-axis corresponding to the provided `colors` array. Example: `(-1.0, 1.5)`. This is only used if `edges` is not provided.
  * `ylim` is as `xlim` but for the y-axis corresponding to the provided `mags` array. Example `(25.0, 20.0)`. This is only used if `edges` is not provided.
  * `nbins::NTuple{2, <:Integer}` is a 2-tuple of integers providing the number of bins to use along the x- and y-axes. This is only used if `edges` is not provided.
  * `xwidth` is the bin width along the x-axis for the `colors` array. This is only used if `edges` and `nbins` are not provided. Example: `0.1`.
  * `ywidth` is as `xwidth` but for the y-axis corresponding to the provided `mags` array. Example: `0.1`.

# Returns

This method returns the Hess diagram as a `StatsBase.Histogram`; you should refer to the StatsBase documentation for more information. In short, if the output of this method is `result`, then the Hess diagram represented as a `Matrix` is available as `result.weights` (this is what you would want for [`fit_templates`](@ref) and similar functions) and the edges of the histogram are available as `result.edges`.
