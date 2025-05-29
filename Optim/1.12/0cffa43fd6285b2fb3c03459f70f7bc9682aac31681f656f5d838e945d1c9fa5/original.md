# SimulatedAnnealing

## Constructor

```julia
SimulatedAnnealing(; neighbor = default_neighbor!,
                     temperature = log_temperature,
                     keep_best::Bool = true)
```

The constructor takes 3 keywords:

  * `neighbor = a!(x_proposed, x_current)`, a mutating function of the current `x`,

and the proposed `x`

  * `T = b(iteration)`, a function of the current iteration that returns a temperature
  * `p = c(f_proposal, f_current, T)`, a function of the current temperature, current

function value and proposed function value that returns an acceptance probability

## Description

Simulated Annealing is a derivative free method for optimization. It is based on the Metropolis-Hastings algorithm that was originally used to generate samples from a thermodynamics system, and is often used to generate draws from a posterior when doing Bayesian inference. As such, it is a probabilistic method for finding the minimum of a function, often over a quite large domains. For the historical reasons given above, the algorithm uses terms such as cooling, temperature, and acceptance probabilities.
