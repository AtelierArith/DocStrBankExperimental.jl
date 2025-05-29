```
weightEM(con_lik_matrix::Array{Float64,2}, θ; conc = 0.0, iters = 500)
```

Takes a conditional likelihood matrix (#categories-by-sites) and a starting frequency vector θ (length(θ) = #categories) and optimizes θ (using Expectation Maximization. Maybe.). If conc > 0 then this gives something like variational bayes behavior for LDA. Maybe.
