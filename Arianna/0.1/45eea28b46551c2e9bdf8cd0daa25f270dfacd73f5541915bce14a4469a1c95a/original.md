```
Metropolis{P,R<:AbstractRNG,C<:Function} <: AriannaAlgorithm
```

A struct representing a Metropolis Monte Carlo algorithm.

# Fields

  * `pools::Vector{P}`: Vector of independent pools (one for each system)
  * `sweepstep::Int`: Number of Monte Carlo steps per sweep
  * `seed::Int`: Random number seed
  * `rngs::Vector{R}`: Vector of random number generators
  * `parallel::Bool`: Flag to parallelise over different threads
  * `collecter::C`: Transducer to collect results from parallelised loops

# Type Parameters

  * `P`: Type of the pool
  * `R`: Type of the random number generator
  * `C`: Type of the transducer
