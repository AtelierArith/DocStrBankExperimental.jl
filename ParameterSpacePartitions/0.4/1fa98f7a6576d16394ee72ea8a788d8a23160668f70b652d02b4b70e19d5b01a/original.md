```
estimate_volume(
    model, 
    p_fun, 
    points, 
    target, 
    bounds,  
    args...;
    n_sim = 10_000,
    kwargs...
)
```

Estimate volume of region with an eillipsoid and hit or miss bias adjustment. 

# Arguments

  * `model`: a model function that returns predictions given a vector of parameters
  * `p_fun`: a function that that evaluates the qualitative data pattern
  * `points`: a p x n matrix of sampled points where p is the number of parameters and n is the number of samples
  * `target`: the target pattern associated with the `points`
  * `bounds`: a vector of tuples representing (lowerbound, upperbound) for each dimension in
  * `args...`: arguments passed to `model` and `p_fun`

# Keywords

  * `n_sim=10_000`: the number of samples for hit or miss bias adjustment
  * `kwargs...`: additional keyword arguments passed to `model` or `p_fun`
