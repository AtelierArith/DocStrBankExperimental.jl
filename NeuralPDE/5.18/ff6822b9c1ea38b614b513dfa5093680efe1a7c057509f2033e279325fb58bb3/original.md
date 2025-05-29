```
DeepGalerkin(in_dims::Int, out_dims::Int, modes::Int, L::Int, activation1::Function,
    activation2::Function, out_activation::Function, strategy::AbstractTrainingStrategy;
    kwargs...)
```

## Arguments:

  * `in_dims`: number of input dimensions = (spatial dimension + 1).
  * `out_dims`: number of output dimensions.
  * `modes`: Width of the LSTM type layer.
  * `L`: number of LSTM type layers.
  * `activation1`: activation fn used in LSTM type layers.
  * `activation2`: activation fn used for the output of LSTM type layers.
  * `out_activation`: activation fn used for the output of the network.
  * `kwargs`: additional arguments to be splatted into [`PhysicsInformedNN`](@ref).

## Examples

```julia
discretization = DeepGalerkin(2, 1, 30, 3, tanh, tanh, identity, QuasiRandomTraining(4_000))
```

## References

Sirignano, Justin and Spiliopoulos, Konstantinos, "DGM: A deep learning algorithm for solving partial differential equations", Journal of Computational Physics, Volume 375, 2018, Pages 1339-1364, doi: https://doi.org/10.1016/j.jcp.2018.08.029
