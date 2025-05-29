```
mlp_to_trop_with_quicksum(linear_maps, bias, thresholds) computes the tropical Puiseux rational function associated to a multilayer perceptron. Uses quicksum operations for tropical objects.

inputs: linear maps: an array containing the weight matrices of the neural network. 
        bias: an array containing the biases at each layer
        thresholds: an array containing the threshold of the activation function at each layer, i.e. the number t such that the activation is of
        the form x => max(x,t).
outputs: an object of type TropicalPuiseuxRational.
```
