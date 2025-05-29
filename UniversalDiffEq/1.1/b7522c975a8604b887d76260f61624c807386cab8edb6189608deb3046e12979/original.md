```
SimpleNeuralNetwork(inputs,outputs; kwargs ...)
```

Builds a neural network object and returns randomly initialized parameter values. The neural network object can be evaluated as a function that takes two arguments: a vector `x` and a named tuple with the neural network weights and biases `parameters`.  

```
# kwargs
```

  * `hidden`: the number of neurons in the hidden layer. The default is 10.
  * `nonlinearity`: the activation function used in the neural network. The default is the hyperbolic tangent function `tanh`.
  * `seed`: random number generator seed for initializing the neural network weights.
