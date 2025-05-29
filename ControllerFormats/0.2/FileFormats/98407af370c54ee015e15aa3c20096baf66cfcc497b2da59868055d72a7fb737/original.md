```
read_NNet(filename::String)
```

Read a neural network stored in [`NNet`](https://github.com/sisl/NNet) format.

### Input

  * `filename` – name of the `NNet` file

### Output

A [`FeedforwardNetwork`](@ref).

### Notes

The format assumes that all layers but the output layer use ReLU activation (the output layer uses the identity activation).

The format looks like this (each line may optionally be terminated by a comma):

1. Header text, each line beginning with "//"
2. Comma-separated line with four values: number of layer operations, number of inputs, number of outputs, maximum layer size
3. Comma-separated line with the layer sizes
4. Flag that is no longer used
5. Minimum values of inputs
6. Maximum values of inputs
7. Mean values of inputs and one value for all outputs
8. Range values of inputs and one value for all outputs
9. Blocks of lines describing the weight matrix and bias vector for a layer; each matrix row is written as a comma-separated line, and each vector entry is written in its own line

The code follows [this implementation](https://github.com/sisl/NeuralVerification.jl/blob/957cb32081f37de57d84d7f0813f708288b56271/src/utils/util.jl#L10).
