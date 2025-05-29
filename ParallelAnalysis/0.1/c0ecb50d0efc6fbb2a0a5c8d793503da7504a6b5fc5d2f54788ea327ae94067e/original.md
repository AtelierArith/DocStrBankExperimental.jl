```
parallel(data, niter, f = fa)
```

Parallel Analysis.

# Arguments

  * `data`
  * `niter` is a size of simulation that generate (normal) random data matrix, calculate R, correlation matrix and its eigen values.
  * `f` Function for dimension reduction. Default is `fa`.

# Values

  * `real` Eigen values from read data.
  * `simulated`, `resampled` Mean of eigen values from simulated data.
  * `simulated_bound`, `resampled_bounds` 2.5th and 97.5th perceintile rank values of simulated eigen values.
  * `iter` Number of iterations (of the simulation).
  * `reduncion_method`
  * `correlation_method`

# Example

```julia
julia> using ParallelAnalysis, Random, StatsPlots
julia> begin Random.seed!(1234)
           a = rand(Uniform(0.5, 2.0), 30)
           b = [sort(rand(Uniform(-3, 3), 4); rev = false) for i in 1:30]
           θ = rand(Normal(0, 1), 3000)
           resp = generate_response(θ, a, b)
       end;

julia> par_fit1 = parallel(resp, 10, x -> fa(x; cor_method = :Polychoric))
Progress: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| Time: 0:00:02
Parallel Analysis:
    Suggested that the number of factors is 1 (based on resampling)
    Suggested that the number of componets is 1 (based on resampling)

julia> plot(par_fit1) # visualize a result of parallel analysis

julia> plot(par_fit1, markershape = :none) # Don't show noisy makers.



```
