```
VLSNSearchIterator(spec, cost_function, enumeration_depth = 2, evaluation_function::Function=HerbInterpret.execute_on_input) = StochasticSearchIterator(
```

Returns an iterator that runs according to the Very Large Scale Neighbourhood Search algorithm.

  * `spec` : array of examples
  * `cost_function` : cost function to evaluate the proposed programs
  * `vlsn_neighbourhood_depth` : the enumeration depth to search for a best program at a time
  * `evaluation_function` : evaluation function that evaluates the program generated and produces an output

The propose function consists of all possible programs of the given `enumeration_depth`. The accept function accepts the program with the lowest cost according to the `cost_function`. The temperature value of the algorithm remains constant over time.
