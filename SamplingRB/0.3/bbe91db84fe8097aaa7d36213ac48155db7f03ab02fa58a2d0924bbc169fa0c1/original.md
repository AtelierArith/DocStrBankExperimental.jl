```
cvar_rbp(B::Vector{Float64}, α::Float64, loss_sampler::Function; maxiters::Int=10000)
```

Compute the investment weights on the assets in order to build a CV@R-`alpha` risk budgeting portfolio given risk appetites in `B` and a function `loss_sampler()` that returns a sample vector of relative losses (from their joint distribution).

The algorithm stops after `maxiters` iterations, that is, after sampling `maxiters` vectors of relative losses.

Returns w :: Vector{Float64}

For more details on the algorithm, see `sgd_Lagrangian`.
