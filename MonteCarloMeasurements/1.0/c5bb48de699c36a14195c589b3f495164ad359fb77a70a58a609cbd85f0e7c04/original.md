This package facilitates working with probability distributions by means of Monte-Carlo methods, in a way that allows for propagation of probability distributions through functions. This is useful for, e.g.,  nonlinear [uncertainty propagation](https://en.wikipedia.org/wiki/Propagation_of_uncertainty). A variable or parameter might be associated with uncertainty if it is measured or otherwise estimated from data. We provide two core types to represent probability distributions: `Particles` and `StaticParticles`, both `<: Real`. (The name "Particles" comes from the [particle-filtering](https://en.wikipedia.org/wiki/Particle_filter) literature.) These types all form a Monte-Carlo approximation of the distribution of a floating point number, i.e., the distribution is represented by samples/particles. **Correlated quantities** are handled as well, see [multivariate particles](https://baggepinnen.github.io/MonteCarloMeasurements.jl/stable/#Multivariate-particles-1) below.

A number of type `Particles` behaves just as any other `Number` while partaking in calculations. Particles also behave like a distribution, so after a calculation, an approximation to the **complete distribution** of the output is captured and represented by the output particles. `mean`, `std` etc. can be extracted from the particles using the corresponding functions `pmean` and `pstd`. `Particles` also interact with [Distributions.jl](https://github.com/JuliaStats/Distributions.jl), so that you can call, e.g., `Normal(p)` and get back a `Normal` type from distributions or `fit(Gamma, p)` to get a `Gamma`distribution. Particles can also be asked for `maximum/minimum`, `quantile` etc. using functions with a prefix `p`, i.e., `pmaximum`. If particles are plotted with `plot(p)`, a histogram is displayed. This requires Plots.jl. A kernel-density estimate can be obtained by `density(p)` is StatsPlots.jl is loaded.

## Quick start

```julia
julia> using MonteCarloMeasurements, Plots

julia> a = π ± 0.1 # Construct Gaussian uncertain parameters using ± (\pm)
Particles{Float64,2000}
 3.14159 ± 0.1

julia> b = 2 ∓ 0.1 # ∓ (\mp) creates StaticParticles (with StaticArrays)
StaticParticles{Float64,100}
 2.0 ± 0.0999

julia> pstd(a)      # Ask about statistical properties
0.09999231528930486

julia> sin(a)      # Use them like any real number
Particles{Float64,2000}
 1.2168e-16 ± 0.0995

julia> plot(a)     # Plot them

julia> b = sin.(1:0.1:5) .± 0.1; # Create multivariate uncertain numbers

julia> plot(b)                   # Vectors of particles can be plotted

julia> using Distributions

julia> c = Particles(500, Poisson(3.)) # Create uncertain numbers distributed according to a given distribution
Particles{Int64,500}
 2.882 ± 1.7
```

For further help, see the [documentation](https://baggepinnen.github.io/MonteCarloMeasurements.jl/stable), the [examples folder](https://github.com/baggepinnen/MonteCarloMeasurements.jl/tree/master/examples) or the [arXiv paper](https://arxiv.org/abs/2001.07625).
