```
abcdemc!(prior, dist!, ϵ_target, varexternal; <keyword arguments>)
```

Run ABC with diffential evolution (de) moves in a Markov chain Monte Carlo setup (mc)  providing posterior samples.

Algorithm needs to converge for an unbiased posterior estimate.

# Arguments

  * `prior`: `Distribution` or `Factored` object specifying the parameter prior.
  * `dist!`: distance function computing the distance (`≥ 0.0`) between model and data,    for given `(θ, ve)` input (`θ` parameters, `ve` external variables, see `varexternal`).
  * `ϵ_target`: final target distance (or more general, target width of the ABC kernel); algorithm    equilibrates to final target distribution (approximate posterior) if `ϵ_target` is reached.
  * `varexternal`: external variables that are passed as second positional argument to `dist!`    and can be used to support the distance computation with fast in-place operations in    a thread-safe manner; objects in `varexternal` can be in-place mutated, even in `parallel` mode,    as each thread will receive its own copy of `varexternal` (if not needed input `nothing`).
  * `nparticles::Int=50`: number of total particles to use for inference in each generation.
  * `generations::Int=20`: number of generations (total iterations) to run the algorithm.
  * `verbose::Bool=true`: if set to `true`, enables verbosity (printout to REPL).
  * `rng=Random.GLOBAL_RNG`: an AbstractRNG object which is used by the inference.
  * `parallel::Bool=false`: if set to `true`, threaded parallelism is enabled; `dist!` must be    thread-safe in such a case, e.g. by making use of `varexternal` (`ve`).

# Examples

```julia-repl
julia> using ABCdeZ, Distributions;
julia> data = 5;
julia> prior = Normal(0, sqrt(10));
julia> model(θ) = rand(Normal(θ, 1));
julia> dist!(θ, ve) = abs(model(θ)-data), nothing;
julia> ϵ = 0.3;
julia> r = abcdemc!(prior, dist!, ϵ, nothing, nparticles=1000, generations=300, parallel=true);
julia> posterior = [t[1] for t in r.P];
```
