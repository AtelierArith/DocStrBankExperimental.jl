```
fit_sfh(MH_model0::AbstractMetallicityModel,
        disp_model0::AbstractDispersionModel,
        models::AbstractMatrix{<:Number},
        data::AbstractVector{<:Number},
        logAge::AbstractVector{<:Number},
        metallicities::AbstractVector{<:Number};
        x0::AbstractVector{<:Number} = <...>
        kws...)
fit_sfh(MH_model0::AbstractMetallicityModel,
        disp_model0::AbstractDispersionModel,
        models::AbstractVector{<:AbstractMatrix{<:Number}},
        data::AbstractMatrix{<:Number},
        logAge::AbstractVector{<:Number},
        metallicities::AbstractVector{<:Number};
        x0::AbstractVector{<:Number} = <...>
        kws...)
```

Returns a [`CompositeBFGSResult`](@ref StarFormationHistories.CompositeBFGSResult) instance that contains the maximum a posteriori (MAP) and maximum likelihood estimates (MLE) obtained from fitting the provided simple stellar population (SSP) templates `models` (with logarithmic ages `logAge = log10(age [yr])` and metallicities `metallicities`) to the provided `data`. The metallicity evolution is modelled using the provided `MH_model0`, whose parameters can be free or fixed, with metallicity dispersion at fixed time modelled by `disp_model0`, whose parameters can be free or fixed.

This method is designed to work best with a grid of stellar models, defined by the outer product of `N` unique entries in `logAge` and `M` unique entries in `metallicities`. See the examples for more information on usage.

We provide several options for age-metallicity relations and mass-metallicity relations that can be used for `MH_model0` and define APIs for users to create new models that will integrate with this function. Similar flexibility is allowed for the metallicity dispersion model `disp_model0`.

The primary method signature uses flattened formats for `models` and `data`. See the notes for the flattened call signature of [`StarFormationHistories.composite!`](@ref) for more details, as well as [`stack_models`](@ref StarFormationHistories.stack_models) that facilitates rearranging the `models` into this flattened format.

# Arguments

  * `MH_model0` is an instance of [`AbstractMetallicityModel`](@ref StarFormationHistories.AbstractMetallicityModel) that defines how the average metallicity stars being formed in the population changes over time. The fittable parameters contained in this instance are used as the initial values to start the optimization.
  * `disp_model0` is an instance of [`AbstractDispersionModel`](@ref StarFormationHistories.AbstractDispersionModel) that defines the distribution of metallicities of stars forming in a fixed time bin (i.e., the dispersion in metallicity around the mean at fixed time). The fittable parameters contained in this instance are used as the initial values to start the optimization.
  * `models` are the template Hess diagrams for the SSPs that compose the observed Hess diagram.
  * `data` is the Hess diagram for the observed data.
  * `logAge::AbstractVector{<:Number}` is the vector containing the effective ages of the stellar populations used to create the templates in `models`, in units of `log10(age [yr])`. For example, if a population has an age of 1 Myr, its entry in `logAge` should be `log10(10^6) = 6.0`.
  * `metallicities::AbstractVector{<:Number}` is the vector containing the effective metallicities of the stellar populations used to create the templates in `models`. These should be logarithmic abundances like [M/H] or [Fe/H]. There are some notes on the [Wikipedia](https://en.wikipedia.org/wiki/Metallicity) that might be useful.

# Keyword Arguments

  * `x0` is the vector of initial guesses for the stellar mass coefficients per *unique* entry in `logAge`. We try to set reasonable defaults, but in most cases users should be calculating and passing this keyword argument. We provide [`StarFormationHistories.construct_x0_mdf`](@ref) to prepare `x0` assuming a constant star formation rate and total stellar mass, which is typically a good initial guess.
  * `kws...` are passed to `Optim.Options` and can be used to control tolerances for convergence.

# Returns

  * This function returns a [`CompositeBFGSResult`](@ref StarFormationHistories.CompositeBFGSResult) that contains the output from both MLE and MAP optimizations, accessible via `result.mle` and `result.map`. These are each instances of [`BFGSResult`](@ref StarFormationHistories.BFGSResult). See the docs for these structs for more information.
