```
optimize_parameters(problem::Problem, beta_and_gamma::Vector{Float64}; niter::Int=128, learning_rate::Float64 = 0.05)
```

Gradient optimization of the QAOA cost function `using Zygote`.

### Input

  * `problem::Problem`: A `Problem` instance defining the optimization problem.
  * `beta_and_gamma::Vector{Float64}`: The vector of initial QAOA parameters.
  * `niter::Int=128` (optional): Number of optimization steps to be performed.
  * `learning_rate::Float64=0.05` (optional): The learning rate of the gradient-ascent method.

### Output

  * `cost`: Final value of the cost function.
  * `params`: The optimized parameters.
  * `probabilities`: The simulated probabilities of all possible outcomes.

### Notes

  * The gradient-ascent method is defined via the parameter update

`params = params .+ learning_rate .* gradient(f, params)[1]`.

### Example

  * For given number of layers `p`, local fields `h` and couplings `J`, define the problem

`problem = QAOA.Problem(p, h, J)` 

and then do

`cost, params, probs = QAOA.optimize_parameters(problem, ones(2p))`.
