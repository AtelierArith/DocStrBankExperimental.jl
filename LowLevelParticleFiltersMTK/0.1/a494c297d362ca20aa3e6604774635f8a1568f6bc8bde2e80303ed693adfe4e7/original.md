```
StateEstimationSolution(kfsol, prob)
```

A solution object that provides symbolic indexing to a `KalmanFilteringSolution` object.

## Fields:

  * `sol`:  a `KalmanFilteringSolution` object.
  * `prob`: a `StateEstimationProblem` object.

## Example

```julia
sol = StateEstimationSolution(kfsol, prob)
sol[model.x]                 # Index with a variable
sol[model.y^2]               # Index with an expression
sol[model.y^2, dist=true]    # Obtain the posterior probability distribution of the provided expression
sol[model.y^2, Nsamples=100] # Draw 100 samples from the posterior distribution of the provided expression
```
