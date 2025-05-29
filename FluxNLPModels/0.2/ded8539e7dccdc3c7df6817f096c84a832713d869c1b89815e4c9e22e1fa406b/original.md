```
FluxNLPModel{T, S, C } <: AbstractNLPModel{T, S}
```

Data structure that makes the interfaces between neural networks defined with [Flux.jl](https://fluxml.ai/) and [NLPModels](https://github.com/JuliaSmoothOptimizers/NLPModels.jl). A FluxNLPModel has fields

# Arguments

  * `meta` and `counters` retain informations about the `FluxNLPModel`;
  * `chain` is the chained structure representing the neural network;
  * `data_train` is the complete data training set;
  * `data_test` is the complete data test;
  * `size_minibatch` parametrizes the size of an training and test minibatches
  * `training_minibatch_iterator` is an iterator over an training minibatches;
  * `test_minibatch_iterator` is an iterator over the test minibatches;
  * `current_training_minibatch` is the training minibatch used to evaluate the neural network;
  * `current_minibatch_test` is the current test minibatch, it is not used in practice;
  * `w` is the vector of weights/variables;
