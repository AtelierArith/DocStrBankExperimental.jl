```
EarthConfig(; constraints=Set{Vector{Bool}}(), num_knots=20, maxit=10, maxorder=2, maxdegree=2,
            knot_penalty=ifelse(maxorder>1, 3, 2), min_r2=0.001, min_coef=0.01,
            prune::Bool=true, refit::Symbol=:lasso)
```

# Keyword arguments

  * `num_knots`: The number of hinge function knots for each variable.
  * `maxit`: The number of basis construction iterations.
  * `constraints`: A set of bit vectors that constrain the combinations of variables that can be used to produce a term.
  * `prune`: If false, perform the basis construction step but do not perform the pruning step.
  * `maxorder`: The maximum number of distinct variables that can be present in a single term.
  * `maxdegree`: The maximum number of hinges for a single variable that can occur in one term
  * `knot_penalty`: A parameter that controls how easily a new term can enter the model.
  * `min_r2`: Terminate the forward pass if the increase in R2 falls below this value.
  * `min_coef`: Terms with standardized coefficient falling below this value are pruned.
  * `prune`: If true, prune the model using the Lasso.
  * `refit`: After pruning, refit the model using either lasso (:lasso) or OLS (:ols).
