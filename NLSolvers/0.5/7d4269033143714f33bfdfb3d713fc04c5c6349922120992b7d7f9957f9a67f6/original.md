# SimulatedAnnealing

## Constructor

```julia
SimulatedAnnealing(; neighbor = default_neighbor, temperature = log_temperature)
```

The constructor takes two keywords:

  * `neighbor = a(x_now, [x_candidate])`, a function that generates a new iterate based on the current
  * `temperature = b(iteration)`, a function of the current iteration that returns a temperature

## Description

Simulated Annealing is a derivative free method for optimization. It is based on the Metropolis-Hastings algorithm that was originally used to generate samples from a thermodynamics system and is often used to generate draws from a posterior when doing Bayesian inference. As such, it is a probabilistic method for finding the minimum of a function, often over a quite large domains. For the historical reasons given above, the algorithm uses terms such as cooling, temperature, and acceptance probabilities.
