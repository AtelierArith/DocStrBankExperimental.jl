```
Control
```

Hyperparameters for the coordinate descent algorithm

# Fields

  * `tol`: Small positive number, default is 1e-4, providing convergence tolerance
  * `seed`: Random seed, default 770. Note that the only randomness in the algorithm is during the initialization of fixed effect parameters (for the data splits in the cross validation)
  * `trace`: Bool, default `false`. If `true`, prints cost and size of active set over the course of the algorithm.
  * `max_iter`: Integer, default 1000, giving maximum number of iterations in the coordinate gradient descent.
  * `max_armijo`: Integer, default 20, giving the maximum number of steps in the Armijo algorithm. If the maximum is reached, algorithm doesn't update current coordinate and proceeds to the next coordinate
  * `act_num`: Integer, default 5. We will only update all of the fixed effect parameters every `act_num` iterations. Otherwise, we update only the parameters in the current active set.
  * `a₀`: a₀ in the Armijo step, default 1.0. See Schelldorfer et al. (2010) for details about this and the next five fields.
  * `δ`: δ in the Armijo step, default 0.1.
  * `ρ`: ρ in the Armijo step, default 0.001.
  * `γ`: γ in the Armijo step, default 0.0.
  * `lower`: Lower bound for the Hessian, default 1e-6.
  * `upper`: Upper bound for the Hessian, default 1e8.
  * `var_int`: Tuple with bounds of interval on which to optimize when updating a diagonal entry of L, default (0, 100). See Optim.jl in section "minimizing a univariate function on a bounded interval"
  * `cov_int`: Tuple with bounds of interval on which to optimize the when updating a non-diagonal entry of L, default (-50, 50). See Optim.jl in section "minimizing a univariate function on a bounded interval"
  * `optimize_method`: Symbol denoting method for performing the univariate optimization, either :Brent or :GoldenSection, default is :Brent
  * `thres`: If an update to a diagonal entry of L is smaller than `thres`, the parameter is set to 0
