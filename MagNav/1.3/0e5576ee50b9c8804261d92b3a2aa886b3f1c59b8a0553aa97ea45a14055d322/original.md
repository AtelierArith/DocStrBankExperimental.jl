```
eval_shapley(m::Chain, x, features::Vector{Symbol},
             N::Int      = min(10000,size(x,1)),
             num_mc::Int = 10)
```

Compute stochastic Shapley effects for global feature importance.

Reference: https://nredell.github.io/ShapML.jl/dev/#Examples-1

**Arguments:**

  * `m`:        neural network model
  * `x`:        `N` x `Nf` data matrix (`Nf` is number of features)
  * `features`: length-`Nf` feature vector (including components of TL `A`, etc.)
  * `N`:        (optional) number of samples (instances) to use for explanation
  * `num_mc`:   (optional) number of Monte Carlo simulations

**Returns:**

  * `df_shap`:       DataFrame of Shapley effects
  * `baseline_shap`: intercept of Shapley effects
