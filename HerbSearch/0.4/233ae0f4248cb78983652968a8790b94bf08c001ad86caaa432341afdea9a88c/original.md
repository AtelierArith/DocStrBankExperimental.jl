```
MHSearchIterator(examples::AbstractArray{<:IOExample}, cost_function::Function, evaluation_function::Function=HerbInterpret.execute_on_input)
```

The `MHSearchIterator` generates programs using the Metropolis-Hastings algorithm.  The search behaviour has the following characteristics:

  * It uses `random_fill_propose` for the `propose` function.
  * The `accept function is`probabilistic`.
  * The `temperature` of the algorithm remains constant over time, ensuring a stable acceptance probability.

# Arguments

  * `examples::AbstractArray{<:IOExample}`: An array of input-output examples used to guide the search.
  * `cost_function::Function`: A function to evaluate the cost of the proposed programs.
  * `evaluation_function::Function=HerbInterpret.execute_on_input`: A function that evaluates the generated program generated and produces an output. Defaults to `HerbInterpret.execute_on_input`.

# Returns

An iterator to generate programs according to the Metropolis Hastings algorithm.
