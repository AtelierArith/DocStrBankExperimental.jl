```
Options(;
    radius = .1, 
    bounds, 
    n_iters, 
    init_parms,
    parallel = false,
    adapt_radius! = adapt!,
    kwargs...
)
```

An object that holds configuration options for the MCMC sampler. 

# Fields

  * `parallel=false`: runs model on threads if true. A speed up is observed if the evaluation

time of the function is 1 ms or greater. 

  * `radius = .10`: the initial radius length for each chain
  * `bounds`: a vector of tuples representing (lowerbound, upperbound) for each dimension in

the parameter space

  * `x_range`: the range of allowable values for each parameter
  * `n_iters`: number of iterations to perform
  * `p_eval`: the function that evalues the model and pattern functions
  * `adapt_radius!=adapt!`: a function in the form of `func(chain, options; kwargs...)` that adapts

the radius. 

  * `init_parms`: a vector of starting points, such as [[.3,.4],[.3,.5]] in the 2 dimensional case.
  * `n_dims`: number of dimensions in parameter space
  * `parm_names`: a vector of symbols corresponding to parameter names. The default is [:p1,:p2,..:pn]
  * `add_iters`: the number of trials to run after merging chains with the same pattern located in the same region
