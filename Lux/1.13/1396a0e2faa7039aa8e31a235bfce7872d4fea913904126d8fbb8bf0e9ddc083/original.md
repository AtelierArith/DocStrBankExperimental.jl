```
StatefulLuxLayer{FT}(model, ps, st)
```

!!! warning
    This is not a Lux.AbstractLuxLayer


A convenience wrapper over Lux layers which stores the parameters and states internally. This is meant to be used in internal implementation of layers.

## Usecases

  * Internal implementation of [`@compact`](@ref) heavily uses this layer.
  * In SciML codebases where propagating state might involving [`Box`ing](https://github.com/JuliaLang/julia/issues/15276). For a motivating example, see the Neural ODE tutorial.
  * Facilitates Nested AD support in Lux. For more details on this feature, see the [Nested AD Manual Page](@ref nested_autodiff).

## Static Parameters

  * If `FT = true` then the type of the `state` is fixed, i.e., `typeof(last(model(x, ps, st))) == st`.
  * If `FT = false` then type of the state might change. Note that while this works in all cases, it will introduce type instability.

## Arguments

  * `model`: A Lux layer
  * `ps`: The parameters of the layer. This can be set to `nothing`, if the user provides the parameters on function call
  * `st`: The state of the layer

## Inputs

  * `x`: The input to the layer
  * `ps`: The parameters of the layer. Optional, defaults to `s.ps`

## Outputs

  * `y`: The output of the layer
