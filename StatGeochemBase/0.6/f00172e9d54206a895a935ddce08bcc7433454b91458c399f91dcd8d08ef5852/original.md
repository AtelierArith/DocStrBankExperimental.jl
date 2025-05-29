```julia
normproduct(μ1, σ1, μ2, σ2)
```

The integral of the product of two normal distributions N[μ1,σ1] * N[μ2,σ2]. This is itself just another Normal distribution! Specifically, one with variance σ1^2 + σ2^2, evaluated at distance |μ1-μ2| from the mean
