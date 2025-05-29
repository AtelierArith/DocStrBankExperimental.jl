```
BootstrapInput(input_data, bootstrap_method::<:TSBootMethod; kwargs...)
BootstrapInput{T <: TSBootMethod}(; kwargs...)
```

Contains the parameters needed to perform block bootstrap of type T to be used by `makedata()`  function. T can be any subtype of TSBootMethod: Stationary, MovingBlock, or CircularBlock.

## Keyword Arguments

  * `input_data`: data to be resampled. Must be a 1-D array
  * `bootstrap_method`: Type of time series bootstrap to use. Must be subtype of TSBootMethod.
  * `n`: size of resampled output data. Default: 100
  * `block_size`: block size to use. Defaults to the optimal block length using `opt_block_length()`

## Examples

```julia
input_data = [1,2,4,3,5,7,6,3];
kwargs = Dict(:n=>20);
input1 = BootstrapInput(input_data, Stationary; kwargs...)

kwargs = Dict(:input_data=>input_data, :n=>20, :block_size=>4);
input2 = BootstrapInput{MovingBlock}(;kwargs...)
```
