```
SASearchIterator(spec, cost_function, initial_temperature=1, temperature_decreasing_factor = 0.99, evaluation_function::Function=HerbInterpret.execute_on_input)
```

Returns an enumerator that runs according to the Simulated Annealing Search algorithm.

  * `spec` : array of examples
  * `cost_function` : cost function to evaluate the programs proposed
  * `initial_temperature` : the starting temperature of the algorithm
  * `temperature_decreasing_factor` : the decreasing factor of the temperature of the time
  * `evaluation_function` : evaluation function that evaluates the program generated and produces an output

The propose function is `random_fill_propose` (the same as for Metropolis Hastings). The accept function is probabilistic but takes into account the tempeerature too.
