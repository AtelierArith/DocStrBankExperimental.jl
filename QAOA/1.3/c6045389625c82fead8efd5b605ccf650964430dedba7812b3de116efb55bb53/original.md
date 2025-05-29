```
optimize_parameters(problem::Problem, beta_and_gamma::Vector{Float64}, algorithm; niter::Int=128)
```

Gradient-free optimization of the QAOA cost function `using NLopt`.

### Input

  * `problem::Problem`: A `Problem` instance defining the optimization problem.
  * `beta_and_gamma::Vector{Float64}`: The vector of initial QAOA parameters.
  * `algorithm`: One of [NLopt's algorithms](https://nlopt.readthedocs.io/en/latest/NLopt_Algorithms/).
  * `niter::Int=128` (optional): Number of optimization steps to be performed.

### Output

  * `cost`: Final value of the cost function.
  * `params`: The optimized parameters.
  * `probabilities`: The simulated probabilities of all possible outcomes.

### Example

  * For given number of layers `p`, local fields `h` and couplings `J`, define the problem

`problem = QAOA.Problem(p, h, J)` 

and then do

`cost, params, probs = QAOA.optimize_parameters(problem, ones(2p), :LN_COBYLA)`.
