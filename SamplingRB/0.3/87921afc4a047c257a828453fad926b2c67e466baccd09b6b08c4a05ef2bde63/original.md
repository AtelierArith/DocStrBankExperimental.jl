```
sgd_Lagrangian(B::Vector{Float64}, α::Float64, loss_sampler::Function;
               maxiters::Int=10000, ϵ::Float64=1e-12, debug::Int=0)
```

Compute the investment exposure on the assets in order to build a CV@R-α  risk budgeting portfolio using a stochastic gradient method on the Lagrangian formulation of the optimization problem, where we set (arbitrarily) the multiplier to one:    `math    min._{v} CV@R_alpha[L(v)] - sum B_i log(v_i)`

This is made possible by the introduction of an auxiliary variable  t which replaces the CVaR by an expectation, for which stochastic gradients are easy to calculate.

The algorithm stops after maxiter iterations.

Because of the logarithms, in order to remain in the correct (and convex) feasible domain for  v  one must ensure all its entries are strictly positive.  This is done using the parameter ϵ, which should be a very small positive number.

debug >= 1  prints the iteration numbers, exposures and current estimate of V@R.

Returns a pair (v, V@R-α)
