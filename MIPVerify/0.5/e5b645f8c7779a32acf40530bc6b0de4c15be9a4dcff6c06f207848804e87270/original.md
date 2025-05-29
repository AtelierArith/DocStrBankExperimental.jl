```julia
struct SkipSequential <: MIPVerify.NeuralNet
```

Represents a sequential (feed-forward) neural net, with `layers` ordered from input to output. Unlike a regular `Sequential` network, this network type supports [`SkipBlock`](@ref)s, which can take input from multiple previous layers. When a `SkipBlock` is encountered, it receives an array of outputs from preceding layers, allowing for skip connections and residual architectures.

## Fields:

  * `layers`
  * `UUID`
