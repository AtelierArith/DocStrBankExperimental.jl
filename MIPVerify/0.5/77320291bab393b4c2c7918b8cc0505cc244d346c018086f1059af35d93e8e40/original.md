```julia
struct SkipBlock <: MIPVerify.Layer
```

A layer that implements a skip connection pattern, commonly used in residual networks (ResNets).

A `SkipBlock` takes multiple input tensors and applies a corresponding transformation layer to each input. The outputs of these transformations are then combined through element-wise addition.

When used within a [`SkipSequential`](@ref), a `SkipBlock` processes inputs from the most recent layers in the network. If the block has `n` layers, it will take the outputs from the last `n` layers as input, in order. For example, with a 2-layer `SkipBlock`:

  * The second layer processes the output from the immediately preceding layer
  * The first layer processes the output from two layers back

Typically used in conjunction with [`SkipSequential`](@ref) to create networks with skip connections, where the outputs from earlier layers can bypass intermediate layers and be combined with later layer outputs.

Example:

```julia
skip_block = SkipBlock([
    Linear(input_size_1, output_size),  # Transform from one path
    Linear(input_size_2, output_size)   # Transform from another path
])
```

## Fields:

  * `layers`
