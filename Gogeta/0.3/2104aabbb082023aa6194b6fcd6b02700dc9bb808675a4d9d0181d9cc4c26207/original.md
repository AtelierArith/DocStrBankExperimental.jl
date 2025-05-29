```
function create_MIP_from_CNN!(jump_model::JuMP.Model, CNN_model::Flux.Chain, cnnstruct::CNNStructure)
```

Creates a mixed-integer optimization problem from a `Flux.Chain` convolutional neural network model. The optimization formulation is saved in the `JuMP.Model` given as an input.

A dummy objective function of 1 is added to the model. The objective is left for the user to define.

The convolutional neural network must follow a certain structure:

  * It must consist of (in order) convolutional and pooling layers, a `Flux.flatten` layer and finally dense layers
  * I.e. allowed layer types: `Conv`, `MaxPool`, `MeanPool`, `Flux.flatten`, `Dense`
  * The activation function for all of the convolutional layers and the dense layers must be `ReLU`
  * The last dense layer must use the `identity` activation function
  * Input size, filter size, stride and padding can be chosen freely

# Parameters

  * `jump_model`: an empty optimization model where the formulation will be saved
  * `CNN_model`: `Flux.Chain` containing the CNN
  * `cnnstruct`: holds the layer structure of the CNN

# Optional Parameters

  * `max_to_mean`: formulate maxpool layers as meanpool layers. This might improve the convex hull of the model (linear relaxation) for use with relaxing walk algorithm.
  * `logging`: print progress info to console.
