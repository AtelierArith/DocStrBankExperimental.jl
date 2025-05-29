```
evaluate_fun!(de, model, proposal))
```

Evaluates the fitness of an arbitrary function called `loglike`. This is used for  point estimation as it does not use a prior distribution.  

# Arguments

  * `de`: differential evolution object
  * `model`: model containing a likelihood function with data and priors
  * `proposal`: the proposed particle
