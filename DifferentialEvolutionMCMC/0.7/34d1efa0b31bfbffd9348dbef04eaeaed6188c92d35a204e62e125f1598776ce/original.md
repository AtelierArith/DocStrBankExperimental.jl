```
compute_posterior!(de, model, proposal)
```

Computes posterior log likelihood of proposal particle. The value -Inf  is returned if the proposal is out of bounds. 

# Arguments

  * `de`: differential evolution object
  * `model`: model containing a likelihood function with data and priors
  * `proposal`: the proposed particle
