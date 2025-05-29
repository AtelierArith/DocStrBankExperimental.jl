```julia
NNStopping(models, opt)
```

[Deep Optimal Stopping](https://arxiv.org/pdf/1908.01602.pdf), S Becker, P Cheridito, A Jentzen3, and T Welti.

## Arguments

  * `models::Vector{Flux.Chain}`: A vector of Flux.Chain where each model corresponds to a specific timestep from the timespan (tspan). The overall length of the vector should be `length(timesteps) - 1`.
  * `opt`: the optimization algorithm to be used to optimize the neural networks. Defaults to `ADAM(0.1)`.

## Example

d = 3 # Number of assets in the stock r = 0.05 # interest rate beta = 0.2 # volatility T = 3 # maturity u0 = fill(90.0, d) # initial stock value delta = 0.1 # delta f(du, u, p, t) = du .= (r - delta) * u # drift sigma(du, u, p, t) = du .= beta * u # diffusion tspan = (0.0, T) N = 9 # discretization parameter dt = T / (N) K = 100.00 # strike price

# payoff function

function g(x, t)     return exp(-r * t) * (max(maximum(x) - K, 0)) end

prob = PIDEProblem(f, sigma, u0, tspan; payoff = g) models = [Chain(Dense(d + 1, 32, tanh), BatchNorm(32, tanh), Dense(32, 1, sigmoid))           for i in 1:N]

opt = Flux.Optimisers.Adam(0.01) alg = NNStopping(models, opt)

sol = solve(prob, alg, SRIW1(); dt = dt, trajectories = 1000, maxiters = 1000, verbose = true) ```
