```
density(proj::Project, nsamples=100_000, rng=Random.default_rng())
```

Displayed a probability density function for how long it will take to complete the project. `nsamples` controls how many samples are used to estimate the distribution, increasing this makes it take longer, but be more accurate. `rng` controls the random number generator to use, you shouldn't normally need to touch this.

[Gadfly.jl](https://github.com/GiovineItalia/Gadfly.jl) is used for the displaying. A [RecipesBase.jl](https://github.com/JuliaPlots/RecipesBase.jl) recipe is also provided and so this can be used with [StatsPlots.jl](https://github.com/JuliaPlots/StatsPlots.jl) similarly: as `StatsPlots.density(proj)`.
