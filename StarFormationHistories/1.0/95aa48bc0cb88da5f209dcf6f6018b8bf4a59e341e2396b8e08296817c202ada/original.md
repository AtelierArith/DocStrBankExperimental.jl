```
sample_sfh(bfgs_result::CompositeBFGSResult, 
           models::AbstractMatrix{<:Number},
           data::AbstractVector{<:Number},
           logAge::AbstractVector{<:Number},
           metallicities::AbstractVector{<:Number},
           Nsteps::Integer;
           ϵ::Real = 0.05, # HMC step size
           reporter = DynamicHMC.ProgressMeterReport(),
           show_convergence::Bool = true,
           rng::AbstractRNG = default_rng())
sample_sfh(bfgs_result::CompositeBFGSResult, 
           models::AbstractVector{<:AbstractMatrix{<:Number}},
           data::AbstractMatrix{<:Number},
           logAge::AbstractVector{<:Number},
           metallicities::AbstractVector{<:Number},
           Nsteps::Integer;
           kws...)
```

Takes the SFH fitting result in `bfgs_result` and uses it to initialize the Hamiltonian Monte Carlo (HMC) sampler from DynamicHMC.jl to sample `Nsteps` independent draws from the posterior.

The primary method signature uses flattened formats for `models` and `data`. See the notes for the flattened call signature of [`StarFormationHistories.composite!`](@ref) for more details, as well as [`stack_models`](@ref StarFormationHistories.stack_models) that facilitates rearranging the `models` into this flattened format.

# Arguments

  * `models, data, logAge, metallicities` are as in [`fit_sfh`](@ref).
  * `Nsteps` is the number of Monte Carlo samples you want to draw.

# Keyword Arguments

  * `ϵ` is the HMC step size. Convergence of the HMC samples is checked after sampling and if a convergence warning is issued, you should decrease this value.
  * `reporter` is a valid reporter type from DynamicHMC.jl, either `NoProgressReport`, `ProgressMeterReport` for a basic progress meter, or `LogProgressReport` for more detailed reporting.
  * `show_convergence` if `true`, will send sample convergence statistics to the default display.
  * `rng` is a `Random.AbstractRNG` sampler instance that will be used when generating the random samples.

# Returns

A `NamedTuple` with two elements:

  * `posterior_matrix` is a `Matrix` with dimensions `(npar, Nsteps)` where `npar` is the number of fitting variables in the problem and is `npar = length(bfgs_result.mle.μ)`. Each column is one independent sample.
  * `tree_statistics` contains convergence statistics that can be viewed with `DynamicHMC.Diagnostics.summarize_tree_statistics`.

# See also

  * [`tsample_sfh`(@ref StarFormationHistories.tsample_sfh) for multi-threaded version.
