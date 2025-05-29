A [`Base.@kwdef`](https://github.com/JuliaLang/julia/blob/79ceb8dbeab1b5a47c6bd664214616c19607ffab/base/util.jl#L514) struct  used to create Parallel Tempering algorithms. 

Fields (see source file for default values):

  * `target`:  The target distribution.
  * `seed`:  The master random seed.
  * `n_rounds`:  The number of rounds to run.
  * `n_chains`:  The number of chains to use (but see also `n_chains_variational`).
  * `n_chains_variational`:  The number of chains to use for a variational leg of parallel tempering. The default value is zero. If the variational argument is not specified, this argument does nothing. Otherwise, a value of zero corresponds to basic single-leg variational parallel tempering, where the number of chains is taken from the `n_chains` argument. A positive value yields "stabilized" two-leg variational parallel tempering. In that case, the number of chains for the prior-reference leg is taken from `n_chains`, and the number of chains for the variational leg is taken from this argument. See https://arxiv.org/abs/2206.00080

  * `reference`:  The reference distribution (e.g. a prior), or if nothing and a fixed reference is needed (i.e. variational inference is disabled or two-legged variational inference is used), then [`default_reference()`](@ref) will be called to automatically determine the reference based on the type of the target.
  * `variational`:  The variational reference family, or nothing to disable variational inference.
  * `checkpoint`:  Whether a checkpoint should be written to disk at the end of each round.

  * `record`: Determine what should be stored from the simulation. A Vector with elements of type [`recorder_builder`](@ref).

  * `checked_round`: The round index where [`run_checks()`](@ref) will be performed. Set to 0 to skip these checks.

  * `multithreaded`: If multithreaded explorers should be allowed. False by default since it incurs an overhead.

  * `explorer`:  The [`explorer`](@ref) to use, or if nothing, will use [`default_explorer()`](@ref) to automatically determine the explorer based on the type of the target.

  * `extractor`:  Passed to [`extract_sample`](@ref) and [`sample_names`](@ref) to determine how samples should be extracted for [`traces`](@ref).

    The value `nothing` signals default behaviour. Use [`LogPotentialExtractor`](@ref) to extract only the log potential.

  * `show_report`: Show sampling report?

  * `extended_traces`: Whether the [`traces`](@ref) and [`disk`](@ref) recorders will store samples for all the chains (extended = true) or just for the target(s) (extended = false).
